# CLI-Agenten und KI-Framework-SDKs

Das Terminal ist die direkteste, ressourcensparendste und am weitesten verbreitete Schnittstelle für Entwickler, Systemadministratoren und automatisierte Skripte. Command Line Interfaces (CLIs) und Terminal-Agenten (wie Aider, Claude Code, Gemini CLI oder mini-SWE-agent) operieren unmittelbar auf dem Dateisystem, rufen Systemkommandos auf und binden sich nahtlos in Unix-Pipelines ein.

Im Unterschied zu grafischen Benutzeroberflächen oder Webanwendungen verlangt die Integration von KI-Framework-SDKs in CLI-Agenten die Beherrschung zweier unterschiedlicher Betriebsmodi:

* **Der Headless- und Pipeline-Modus (Unix-Philosophie):** Der Agent agiert als nicht-interaktives Glied in einer Kette von Shell-Befehlen (`stdin` ➔ Verarbeitung ➔ `stdout`). Hier sind formatierte Farben und Ladebalken verboten; gefordert sind rein maschinenlesbare Datenströme (Text oder NDJSON).
* **Der interaktive TUI-Modus (Terminal User Interface):** Arbeitet ein Mensch direkt mit dem Agenten, verlangt das Terminal nach einer ergonomischen Oberfläche: farbliches Token-Streaming, Tastaturnavigation, dynamische Statusanzeigen und interaktive Abfragen (REPL-Loop).

```
┌─────────────────────────────────────────────────────────────┐
│                 Eingabe-Kanal (Input Layer)                 │
│  ├─ Interaktiv: Tastatur-Eingabe / REPL / TUI               │
│  └─ Headless: Pipe aus Standard-Input (`stdin` / Script)    │
└──────────────────────────────┬──────────────────────────────┘
                               │
┌──────────────────────────────▼──────────────────────────────┐
│ CLI-Architektur & Router (Framework-SDK)                    │
│  ├─ TTY-Erkennung (`isatty()`) ➔ Modus-Umschaltung         │
│  ├─ Subprozess-Manager (PTY-Spawning, Execution Sandboxing) │
│  └─ Kontext-Sammler (Git-Status, Dateiinhalte, Umgebung)    │
└──────────────────────────────┬──────────────────────────────┘
                               │ Typsichere Modell-Inferenz
┌──────────────────────────────▼──────────────────────────────┐
│ KI-Modell-Laufzeit (Lokales Ollama / Cloud-Endpunkt)        │
└──────────────────────────────┬──────────────────────────────┘
                               │
         ┌─────────────────────┴─────────────────────┐
         ▼                                           ▼
┌─────────────────────────────────┐ ┌─────────────────────────────────┐
│ Ausgabe: Maschinell (`stdout`)  │ │ Ausgabe: Menschlich (`stderr`)  │
│ Reiner Code, strukturierter JSON│ │ Status-Balken, Linter-Meldungen,│
│ für nachfolgende Shell-Pipes    │ │ ANSI-Farben, interaktive TUIs   │
└─────────────────────────────────┘ └─────────────────────────────────┘
```

---

## Kernaufgaben der CLI-Agenten-Integration

1. **Strikte Kanaltrennung (`stdout` vs. `stderr`):** Maschinelle Ergebnisse gehören ausschließlich auf den Standard-Ausgabe-Kanal (`stdout`). Diagnosemeldungen, Ladebalken und Protokolle müssen zwingend auf den Fehlerkanal (`stderr`) umgeleitet werden, um nachgelagerte Unix-Pipes (`| jq`) nicht zu zerstören.
2. **Sichere Subprozess-Ausführung:** Führt der Agent Shell-Kommandos aus, müssen Shell-Injections hardwarenah verhindert und Prozesse über Timeouts und Signal-Handler (`SIGINT`) kontrollierbar bleiben.
3. **Unterbrechbarkeit (Graceful Interruption):** Drückt ein Entwickler `Ctrl + C`, darf der Prozess nicht unsauber abbrechen, sondern muss die laufende Modell-Inferenz stoppen, den Terminal-Zustand zurücksetzen und temporäre Dateien bereinigen.

---

## Unterkategorien dieses Kapitels

Die folgenden drei Abschnitte analysieren die technischen Anforderungen im Terminal im Detail:

* [Unix-Pipes, Headless-Betrieb und Standard-Streams](cli-agenten-ki-integration/unix-pipes-headless.md): Die Unix-Philosophie im KI-Zeitalter, TTY-Erkennung, Trennung von `stdout` und `stderr` sowie automatisierte Script-Pipelines.
* [TUI-Schnittstellen, REPL-Loops und Token-Streaming](cli-agenten-ki-integration/tui-repl-terminal-streaming.md): Interaktive Oberflächen (Ratatui, Bubbletea, Textual), ANSI-Escape-Sequenzen, Syntax-Highlighting und Signal-Handling.
* [Subprozess-Steuerung, PTYs und Shell-Sicherheit](cli-agenten-ki-integration/subprozess-pty-sicherheit.md): Ausführung lokaler Werkzeuge über Pseudo-Terminals (PTYs), Schutz vor Shell-Injection und Timeout-Überwachung.

---

> [!NOTE]
> Die qualitative Gegenüberstellung populärer Coding-Agenten im Terminal findet sich im Kapitel [KI- und CLI-Coding-Agenten im Vergleich](cli-agenten.md).
