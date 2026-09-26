# KI- und CLI-Coding-Agenten im Vergleich

Dieses Kapitel vertieft den praktischen Einsatz moderner Terminal- und Coding-Agenten
für die Entwicklung und Dokumentationspflege. Es grenzt die Generationen und Werkzeuge
voneinander ab und beleuchtet insbesondere die Übergänge zwischen Befehlsassistenz,
autonomen Terminal-Agenten und Multi-Agenten-Plattformen.

## Generationen und Paradigmen

Die Entwicklung der Entwicklerwerkzeuge im Terminal gliedert sich in drei wesentliche Stufen:

| Stufe | Paradigma | Arbeitsweise | Typische Vertreter |
| --- | --- | --- | --- |
| 1. Befehlshelfer | Einzelfragen & Snippets | Übersetzt natürliche Sprache in Shell-Befehle, erklärt Syntax | OpenAI Codex CLI, GitHub Copilot in the CLI (`gh copilot`) |
| 2. Autonomer Einzel-Agent | Repo-Bearbeitung im Loop | Analysiert Dateien, editiert Code, führt Tests aus, committet | Claude Code, [Aider](docs-as-code/agentische-pflege.md), [Cline](docs-as-code/agentische-pflege.md) |
| 3. Multi-Agenten-Plattform | Orchestrierung & Asynchronität | Spawnt Subagenten, Hintergrund-Builds, Skills, MCP, IDE-Brücke | AGY CLI (`agy`), [LangGraph](docs-as-code/agentische-pflege.md) |

---

## 1. Befehlshelfer: Wo hören sie auf?

Werkzeuge wie die historische **OpenAI Codex CLI** oder **GitHub Copilot CLI** (`gh copilot`) arbeiten nach dem klassischen Frage-Antwort-Prinzip:

- **Stärken:** Schnelles Nachschlagen von Shell-Befehlen, Git-Optionen, `jq`-Filtern oder Regex-Mustern direkt im Terminal.
- **Grenze:** Sie besitzen kein Gedächtnis über den gesamten Projektzusammenhang, bearbeiten keine Dateien autonom über mehrere Iterationen und führen keine Fehleranalysen anhand von Compiler- oder Testausgaben durch.

---

## 2. Autonome Terminal-Agenten: Wo hören sie auf?

Werkzeuge wie **Claude Code** (Anthropic) oder Open-Source-Vertreter wie [Aider](docs-as-code/agentische-pflege.md) und [Cline](docs-as-code/agentische-pflege.md) greifen aktiv auf das Dateisystem und die Kommandozeile zu:

- **Stärken:**
  - Durchsucht Repositories eigenständig (`grep`, Dateibäume, semantische Indexierung).
  - Führt Änderungen an mehreren Dateien durch, startet Test- und Build-Suites und korrigiert Fehler iterativ.
  - Erstellt saubere Git-Branches und Commit-Nachrichten.
- **Grenze:**
  - Sie agieren primär als **sequenzieller Einzel-Agent**.
  - Parallele, voneinander getrennte Teilaufgaben (z. B. eine aufwendige Dokumentenrecherche im Hintergrund, während der Hauptagent den Code refaktoriert) sind nicht nativ modular entkoppelt.
  - Häufig enge Bindung an ein proprietäres Ökosystem oder begrenzte Protokoll-Erweiterbarkeit.

---

## 3. Agenten-Plattformen und Multi-Agenten-Systeme

Die **Antigravity CLI** (`agy`) von Google DeepMind sowie Multi-Agenten-Frameworks wie [LangGraph](docs-as-code/agentische-pflege.md) erweitern das Modell um System- und Orchestrierungsfähigkeiten:

- **Subagenten & Delegation:** Der Hauptagent kann spezialisierte Unteragenten für Teilaufgaben (wie Codebase-Recherche oder Dokumentationsanalysen) beauftragen.
- **Asynchrone Hintergrund-Tasks:** Langlaufende Builds (wie `mdbook build`) oder Server laufen asynchron im Hintergrund, während der Entwickler weiter interagieren kann.
- **Modulare Erweiterbarkeit:**
  - **Skills:** Wiederverwendbare Handlungsanweisungen und Toolsets (`SKILL.md`).
  - **Model Context Protocol (MCP):** Standardisierte Schnittstelle zu externen Werkzeugen und Datenquellen.
  - **Regeln und Hooks:** Projektbezogene Richtlinien für Codequalität und Dokumentation.
- **Verzahnung:** Nahtloser Wechsel zwischen reinem Terminal-Betrieb (`agy`), Standalone-IDE und grafischer Agenten-Arbeitsumgebung (Antigravity 2.0).

---

## Einsatz in Docs-as-Code und Wissenssystemen

Für dateibasierte Dokumentations- und Buchprojekte (wie dieses mdBook) ergeben sich klare Einsatzbereiche:

1. **Strukturprüfung:** Agenten prüfen automatisch interne Links, Tabellenkonsistenz und Metadaten.
2. **Review & Aktualisierung:** Dokumente werden bei Codeänderungen im selben Commit-Zyklus synchron gehalten (siehe [Agentische Dokumentationspflege](docs-as-code/agentische-pflege.md)).
3. **Menschliche Kontrolle:** Auch agentische Werkzeuge ersetzen nicht das fachliche Review. Ein deterministischer Build (`mdbook build`) und versionskontrollierte Quelltexte bleiben die verbindliche Grundlage.

---

## Verwandte Kapitel

- [Agentische Dokumentationspflege](docs-as-code/agentische-pflege.md): Geprüfte Open-Source-Werkzeuge mit Dateipersistenz.
- [KI-Unterstützung und dokumentengestützte Suche](docs-as-code/ki-unterstuetzung.md): Integration von KI in Docs-as-Code.
- [Architekturen im Zusammenhang](architekturen.md): Zusammenspiel von Wissenssystemen, CMS und Docs-as-Code.
