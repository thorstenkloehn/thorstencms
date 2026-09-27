# Unix-Pipes, Headless-Betrieb und Standard-Streams

Die Unix-Philosophie – Programme zu entwerfen, die genau eine Aufgabe beherrschen, textbasierte Datenströme verarbeiten und nahtlos über Pipes verkettet werden können – behält auch im Zeitalter generativer Sprachmodelle ihre Gültigkeit. Wenn Entwickler und CI/CD-Pipelines KI-gestützte Werkzeuge auf der Kommandozeile einsetzen, scheitern viele existierende Tools daran, dass sie unkontrolliert Statusmeldungen, ANSI-Farben oder Ladebalken in den Datenstrom mischen.

Ein robuster CLI-Agent, der auf einem modernen KI-Framework-SDK aufbaut, muss sich als verlässliches Werkzeug in Shell-Pipelines einfügen. Das verlangt eine saubere Trennung der Standard-Streams, die automatische Erkennung des Ausführungskontexts (TTY vs. Pipe) sowie maschinenlesbare Streaming-Formate.

---

## Architektur des Headless-Datenstroms

Im Headless- und Pipeline-Modus interagiert der CLI-Agent nicht mit einer menschlichen Tastatur, sondern konsumiert Daten aus dem Standard-Eingabekanal (`stdin`) und leitet die Inferenz-Ergebnisse direkt an nachgelagerte UNIX-Werkzeuge weiter (`stdout`).

```
┌────────────────────────────────────────────────────────────────────────┐
│ UNIX-Pipeline-Architektur                                              │
│                                                                        │
│   [ git diff / cat file ]                                              │
│              │                                                         │
│              ▼ (stdin)                                                 │
│   ┌────────────────────────────────────────────────────────────┐       │
│   │ CLI-Agent (Headless-Modus)                                 │       │
│   │  ├─ TTY-Erkennung: `isatty(stdin) == false`                │       │
│   │  ├─ Deaktivierung von Farben & Cursor-Sequenzen           │       │
│   │  ├─ Aggregation oder Streaming des Payloads                │       │
│   │  └─ Framework-SDK: Typsichere Prompt-Inferenz              │       │
│   └───┬────────────────────────────────────────────────────┬───┘       │
│       │ (stdout: Reiner Nutzdatenstrom)                    │           │
│       ▼                                                    ▼           │
│   [ jq / sponge / git apply ]                   [ stderr: Logging ]    │
│   Maschinenlesbare Weiterverarbeitung           Metadaten, Token/s,    │
│   (Reiner Code, JSON, Plaintext)                Fehler & Kosten-Warnung│
└────────────────────────────────────────────────────────────────────────┘
```

---

## TTY-Erkennung und Kontext-Umschaltung

Ein KI-CLI-Werkzeug muss beim Prozessstart feststellen, ob Ein- und Ausgänge mit einem interaktiven Benutzerterminal (Teletypewriter / TTY) verbunden sind oder ob Daten über Pipes umgeleitet werden.

### Erkennungsmechanismus

In modernen Programmiersprachen erfolgt die Prüfung über Low-Level-Systemaufrufe:

* **Python:** `sys.stdin.isatty()` und `sys.stdout.isatty()`
* **Node.js:** `Boolean(process.stdin.isTTY)` und `Boolean(process.stdout.isTTY)`
* **Rust:** `std::io::stdin().is_terminal()` (ab Rust 1.70)
* **Go:** `term.IsTerminal(int(os.Stdin.Fd()))`

### Verhaltensregeln nach Erkennung

| Zustand | Erkennung | Eingabequelle | Ausgabeformat | Logging / Fortschritt |
| :--- | :--- | :--- | :--- | :--- |
| **Interaktiver Modus** | `stdin.isatty() == true` | Tastatur (REPL / Prompt) | ANSI-Farben, Markdown, TUI | In TUI integriert |
| **Consumer-Pipe** | `stdin.isatty() == false` | Eingangs-Pipe (`cat \| agent`) | Gemäß Flag (`--raw`, `--json`) | `stderr` (kein Spinner) |
| **Producer-Pipe** | `stdout.isatty() == false` | Beliebig | Reiner Text / JSON (keine ANSI-Codes) | Strikt `stderr` |
| **Reines Scripting** | Beide `false` | Skript / Datei-Deskriptor | Deterministic Plaintext / NDJSON | Strikt `stderr` |

---

## Strikte Kanaltrennung: `stdout` vs. `stderr`

Die goldene Regel robuster Shell-Programmierung besagt: **Niemals diagnostische Ausgaben auf `stdout` schreiben.**

1. **`stdout` (File Descriptor 1):** Dient ausschließlich dem Nutzdaten-Ergebnis des Modells. Wenn der Agent aufgefordert wird, ein Refactoring vorzunehmen oder ein JSON-Objekt zu erzeugen, darf auf `stdout` kein einziges zusätzliches Zeichen (wie `Lade Modell...` oder `Antwort empfangen:`) ausgegeben werden. Jedes unerwartete Zeichen zerstört nachfolgende Parser wie `jq`, `patch` oder Compiler.
2. **`stderr` (File Descriptor 2):** Hierhin gehören alle Diagnosen, Kostenkalkulationen, Token-Zähler (z. B. `Inferenz: 42 tokens/s`), Warnhinweise und Fehler. Auch Ladebalken oder Fortschrittsanzeigen (sofern im Batch-Modus überhaupt gewünscht) dürfen ausschließlich nach `stderr` geschrieben werden.

### Pufferung und Flushing bei Streaming

Wird das Modell-Ergebnis zeichen- oder tokenweise gestreamt, muss der CLI-Agent beachten, dass Standard-C-Bibliotheken Ausgaben auf blockorientierten Geräten (wie Pipes) puffern (meist 4 KB bis 8 KB Puffergröße). Ohne explizites Leeren (`flush()`) nach jedem Token-Chunk empfängt das nachgelagerte Programm die Daten stoßweise statt kontinuierlich:

* Nach jedem geschriebenen Streaming-Fragment muss ein expliziter Flush auf den Ausgabekanal erfolgen (`sys.stdout.flush()` bzw. `fflush(stdout)`).

---

## Maschinenlesbare Austauschformate: NDJSON

Für komplexe Agenten-Workflows, bei denen der CLI-Agent Zwischenschritte, Tool-Aufrufe und finale Antworten zurückliefert, eignet sich **Newline-Delimited JSON (NDJSON)** oder JSON-Lines (`.jsonl`). Jedes Ereignis wird als vollständiges JSON-Objekt in einer einzelnen Zeile ausgegeben:

```json
{"type": "step_start", "step": 1, "tool": "file_search"}
{"type": "tool_call", "name": "ripgrep", "query": "auth_token"}
{"type": "tool_result", "matches": 3}
{"type": "content_delta", "delta": "Ich habe die Token-Definition gefunden."}
{"type": "done", "total_tokens": 842, "cost_usd": 0.0012}
```

Nachfolgende Programme in der Pipe können diese Zeilen streaming-fähig mit Werkzeugen wie `jq --unbuffered` oder benutzerdefinierten Parsern verarbeiten, ohne auf das Ende der gesamten Generierung warten zu müssen.

---

## Exit-Codes und Signal-Behandlung

Ein sauberes CLI-Werkzeug signalisiert Erfolg oder Misserfolg über standardisierte Unix-Rückgabewerte (Exit-Codes):

* **`0` (Success):** Die Inferenz bzw. Transformation wurde fehlerfrei abgeschlossen.
* **`1` (General Error):** Unerwarteter Laufzeitfehler (z. B. Modell-API nicht erreichbar).
* **`2` (Usage Error):** Ungültige CLI-Argumente, fehlende Umgebungsvariablen oder inkompatible Flag-Kombinationen.
* **`124` (Timeout):** Das Modell oder ein Subprozess hat das konfigurierte Zeitlimit überschritten.
* **`130` (Interrupted by SIGINT):** Der Benutzer oder ein Prozess-Manager hat die Ausführung mit `Ctrl + C` bzw. Signal 2 abgebrochen.

Durch die Einhaltung dieser Codes können Orchestrierungswerkzeuge wie Makefiles, Bash-Skripte oder CI-Runner zuverlässig über `set -e` oder `|| exit $?` auf Fehler reagieren.

---

## Querverweise und Vertiefung

* Für interaktive Benutzeroberflächen im Terminal mit Cursor-Steuerung und TUI-Frameworks siehe [TUI-Schnittstellen, REPL-Loops und Token-Streaming](tui-repl-terminal-streaming.md).
* Zur sicheren Ausführung von Systemkommandos durch den Agenten siehe [Subprozess-Steuerung, PTYs und Shell-Sicherheit](subprozess-pty-sicherheit.md).
* Den konzeptionellen Vergleich populärer Terminal-Agenten (Aider, Claude Code, Gemini CLI) behandelt das Kapitel [KI- und CLI-Coding-Agenten im Vergleich](../cli-agenten.md).
