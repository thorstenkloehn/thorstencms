# TUI-Schnittstellen, REPL-Loops und Token-Streaming

Während Automatisierungsskripte und Unix-Pipes minimale, unformatierte Textströme fordern, verlangt die direkte Mensch-Maschine-Interaktion auf der Kommandozeile nach einer reaktiven, übersichtlichen und ergonomischen Umgebung. Moderne Terminal User Interfaces (TUIs) verwandeln einfache CLI-Skripte in vollwertige Arbeitsumgebungen mit Syntax-Hervorhebung, mehrzeiligen Eingabefeldern, interaktiven Bestätigungsdialogen und flüssigem Token-Streaming.

Die Integration eines KI-Framework-SDKs in eine TUI erfordert jedoch eine präzise Koordination zwischen asynchronem Netzwerk-I/O, Ereignis-Schleifen der Benutzeroberfläche und der physischen Steuerung des Terminal-Zustands.

---

## Architektur eines agentischen REPL-Loops

Ein interaktiver Coding-Agent arbeitet nach dem Prinzip einer erweiterten Read-Eval-Print-Loop (REPL). Im Unterschied zu klassischen Programmiersprachen-REPLs (wie Python oder Node.js) schiebt der Agent zwischen Eingabe und Ausführung komplexe Kontext-Analysen, asynchrone Modell-Anfragen und Werkzeug-Genehmigungen ein.

```
┌────────────────────────────────────────────────────────────────────────┐
│ Agentischer REPL-Zustandsgraph                                         │
│                                                                        │
│   ┌───────────────┐        Eingabe        ┌────────────────────────┐   │
│   │               ├──────────────────────►│  Kontext-Aggregation   │   │
│   │  Read (REPL)  │                       │  (Git, Files, Memory)  │   │
│   │               │◄─────────────────┐    └───────────┬────────────┘   │
│   └───────▲───────┘                  │                │                │
│           │                          │                ▼                │
│           │ Reset / Next             │    ┌────────────────────────┐   │
│           │                          │    │  Modell-Inferenz &     │   │
│   ┌───────┴───────┐                  │    │  Token-Streaming       │   │
│   │               │                  │    └───────────┬────────────┘   │
│   │ Print / State │                  │                │                │
│   │               │                  │                ▼ Tool Call?     │
│   └───────▲───────┘                  │    ┌────────────────────────┐   │
│           │                          └────┤  Human-in-the-Loop     │   │
│           │ Durchgeführt                  │  Diff-Bestätigung      │   │
│   ┌───────┴───────┐     (Abbruch)         └───────────┬────────────┘   │
│   │ Subprozess-   │◄──────────────────────────────────┘ (Freigabe)     │
│   │ Ausführung    │                                                    │
│   └───────────────┘                                                    │
└────────────────────────────────────────────────────────────────────────┘
```

---

## Terminal-Steuerung: Raw Mode vs. Cooked Mode

Standardmäßig operieren Terminals im zeilenorientierten Modus (**Canonical / Cooked Mode**). Eingaben werden vom Betriebssystem gepuffert, bis der Nutzer die Eingabetaste drückt. Das Terminal kümmert sich eigenständig um Zeileneditierung und Zeichen-Echo.

Für eine moderne TUI muss das Programm in den **Raw Mode** wechseln:

1. **Deaktivierung von Pufferung und Echo:** Jeder Tastenanschlag (einschließlich Pfeiltasten, Tabulatoren, `Ctrl + C`, `Escape`) wird sofort ohne Verzögerung an das Programm übermittelt.
2. **Eigenverantwortliche Darstellung:** Das Framework muss Cursor-Positionierung, Zeilenumbrüche und das Rendern von Zeichen selbst verwalten.
3. **Bracketed Paste Mode:** Ermöglicht das Einfügen mehrzeiliger Codeblöcke aus der Zwischenablage, ohne dass Zeilenumbrüche versehentlich als sofortige Ausführungsbefehle interpretiert werden.

### Alternate Screen Buffer vs. Inline-Streaming

Es existieren zwei grundlegende Design-Paradigmen für Terminal-Agenten:

| Kriterium | Fullscreen-TUI (Alternate Screen) | Inline-Streaming (Standard Scrollback) |
| :--- | :--- | :--- |
| **Mechanismus** | ANSI-Code `\x1b[?1049h` / `\x1b[?1049l` | Direkte Ausgabe im normalen Verlauf |
| **Typische Vertreter** | LazyGit, K9s, Textual-Vollbild-Apps | Aider, Claude Code, Gemini CLI |
| **Scrollback-Verhalten** | Eigener Buffer; nach Beenden ist der alte Terminal-Inhalt wieder sichtbar | Generierter Code verbleibt dauerhaft in der Shell-Historie |
| **Kopieren & Einfügen** | Erfordert native TUI-Mausintegration | Standard-Mausmarkierung des Terminals funktioniert |
| **Eignung für Coding-Agenten** | Gut für visuelle Dashboards und Explorer | **Optimal** für Coding-Sessions, da Ausgaben referenzierbar bleiben |

Moderne Coding-Agenten bevorzugen das **Inline-Streaming**, damit Code-Auszüge, Diffs und Antworten des Modells nach Abschluss des Dialogs nahtlos in der Shell-Historie des Nutzers erhalten bleiben.

---

## Relevante TUI-Frameworks nach Ökosystem

Für den Bau performanter und plattformübergreifender Terminal-Oberflächen haben sich spezialisierte Bibliotheken etabliert:

* **Rust:**
  * **Ratatui (Fork von tui-rs):** Der De-facto-Standard für hardwarenahe, extrem performante Terminal-UIs mit sofortigem Rendering (Immediate Mode).
  * **Crossterm:** Plattformunabhängige Low-Level-Bibliothek zur Manipulation von Cursor, Farben und Terminal-Events auf Linux, macOS und Windows.
* **Go:**
  * **Bubbletea (Charm):** Basiert auf der Elm-Architektur (Model-Update-View) und erlaubt deklarative, hochgradig modulare TUI-Komponenten mit hervorragender Async-Unterstützung.
  * **Lipgloss:** Deklaratives Styling für Ränder, Farben und Layouts im Terminal.
* **Python:**
  * **Textual:** Modernes, ereignisgesteuertes Framework mit CSS-ähnlichem Styling und Widget-System.
  * **Prompt-Toolkit:** Ausgezeichnet für mehrzeilige Eingabe-Prompts mit Autovervollständigung, Syntax-Highlighting und Emacs-/Vi-Tastenbelegung.
  * **Rich:** Perfekt für progressives Inline-Rendering von Markdown, Tabellen und Statusanzeigen.
* **Node.js / TypeScript:**
  * **Ink:** Ermöglicht den Bau von CLI-UIs unter Verwendung von React-Komponenten und Flexbox-Layouts.

---

## Progressive Markdown-Formatierung und Streaming

Wenn Sprachmodelle Antworten tokenweise generieren, treffen unvollständige Markdown-Fragmente im Millisekundentakt ein. Eine naive Darstellung führt zu störendem Bildschirmflackern oder fehlerhaften Formatierungen (z. B. wenn öffnende Backticks ` ```typescript ` empfangen wurden, der schließende Block aber noch fehlt).

### Streaming-Renderer-Architektur

1. **Differentieller Puffer:** Eingehende Chunks werden in einem internen Puffer akkumuliert.
2. **Zeilenbasierte Ausgabe:** Solange eine Textzeile noch nicht durch einen Zeilenumbruch abgeschlossen ist, wird sie im Terminal mittels Carriage Return (`\r`) und Zeilenlöschung (`\x1b[2K`) an Ort und Stelle aktualisiert.
3. **Syntax-Highlighting von Codeblöcken:** Erkennt der Parser den Beginn eines Code-Blocks, wird der nachfolgende Inhalt zeilenweise an einen Lexer (z. B. Syntect in Rust, Chroma in Go oder Pygments in Python) übergeben und mit ANSI-Farbcodes formatiert ausgegeben.

---

## Signal-Handling: `Ctrl + C` und Aufräumarbeiten

Nichts frustriert Anwender mehr als ein abgestürztes Terminal, in dem der Cursor verschwunden ist oder Eingaben unsichtbar bleiben, weil das Programm im Raw Mode abgebrochen wurde.

Ein robuster Agent implementiert gestaffelte Signal-Handler für `SIGINT` (Signal 2):

```
[ Laufende Modell-Inferenz oder Subprozess ]
                   │
                   ▼  Erstes Ctrl + C (SIGINT)
[ Inferenz abbrechen / Subprozess terminieren ]
[ Terminal bleibt aktiv, Eingabe-Prompt kehrt zurück ]
                   │
                   ▼  Zweites Ctrl + C (innerhalb 1s) oder Ctrl + D
[ Graceful Shutdown: Cursor wieder einblenden, Raw Mode beenden, Exit 0 ]
```

### Aufräumpflicht bei Programmende

Vor jedem Programmende – egal ob regulär, durch Abbruchsignal oder durch eine Panic/Exception – müssen folgende Terminal-Befehle zwingend ausgeführt werden (idealerweise über Panic-Hooks oder Destruktoren):

1. **Cursor wieder sichtbar schalten:** `\x1b[?25h`
2. **Raw Mode verlassen:** Terminal-Attribute (`termios`) auf die gesicherten Ursprungswerte zurücksetzen.
3. **Alternate Screen verlassen:** Sofern verwendet, `\x1b[?1049l` ausgeben.

---

## Querverweise und Vertiefung

* Wie nicht-interaktive Pipelines ohne TUI implementiert werden, erläutert [Unix-Pipes, Headless-Betrieb und Standard-Streams](unix-pipes-headless.md).
* Die Absicherung von Subprozessen und interaktive Bestätigungsdialoge vertieft das Kapitel [Subprozess-Steuerung, PTYs und Shell-Sicherheit](subprozess-pty-sicherheit.md).
* Konzepte zur Visualisierung von Inline-Diffs und Code-Patches finden sich unter [Inline-Diff-Patching und AST-Refactoring](../ide-ki-integration/inline-diff-patching.md).
