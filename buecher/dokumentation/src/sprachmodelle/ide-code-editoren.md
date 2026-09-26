# Sprachmodelle in IDEs und Code-Editoren

[Übergeordnete Kategorie: Integration von Sprachmodellen in Software-Architekturen](../sprachmodell-integration.md)

KI-gestützte Codevervollständigung, kontextbezogene Chat-Assistenten, Inline-Refactorings und autonome Entwickler-Workflows direkt in der Entwicklungsumgebung.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [VSCodium](https://github.com/VSCodium/vscodium) | MIT | Sehr hoch | Vollständig offene Binärdistribution von Visual Studio Code mit freier Erweiterungs-Registry für LLM- und Coding-Plugins. | Dateien: [Lokale Workspace-Dateien und JSON-Konfiguration (.vscode/settings.json)](https://vscodium.com/) |
| 2 | [Zed](https://github.com/zed-industries/zed) | GPL-3.0 / Apache-2.0 | Hoch | Moderner Hochleistungs-Code-Editor in Rust mit nativer Modellunterstützung, Inline-Assistenten und Ollama-/API-Schnittstellen. | Dateien: [Workspace-Dateien und JSON-Konfigurationsdateien](https://zed.dev/docs/assistant) |
| 3 | [Continue](https://github.com/continuedev/continue) | Apache-2.0 | Hoch | Offene Assistenten-Erweiterung für IDEs mit Tab-Autovervollständigung, Chat-Panel und flexibler Modellauswahl. | Dateien: [Lokale Konfigurationsdateien (.continue/config.yaml) und Workspace-Dateien](https://docs.continue.dev/) |
| 4 | [Eclipse Theia](https://github.com/eclipse-theia/theia) | EPL-2.0 | Hoch | Modulare Plattform für Cloud- und Desktop-IDEs mit Theia AI-Framework zur Erstellung domänenspezifischer KI-Werkzeuge. | Dateien: [Workspace-Dateisystem und JSON-Konfiguration](https://theia-ide.org/docs/) |
| 5 | [avante.nvim](https://github.com/yetone/avante.nvim) | Apache-2.0 | Mittel | Leistungsfähiges Neovim-Plugin für Cursor-ähnliche KI-Assistenz im Terminal mit automatischem Diff-Abgleich und Multi-Provider-Support. | Dateien: [Lokale Workspace-Dateien und Lua-Konfigurationsdateien](https://github.com/yetone/avante.nvim) |

## Einsatz und Abgrenzung

Entwicklungsumgebungen integrieren Sprachmodelle direkt in die Arbeitsflüsse von Entwicklerinnen und Entwicklern, müssen dabei jedoch Datenhoheit und Reproduzierbarkeit wahren.

- **VSCodium:** Die Distribution und ihre Erweiterungen separat prüfen; installierte Assistenten können Daten an Modellanbieter übertragen.
- **Zed:** Editor mit integrierter Modellanbindung; unterstützt sowohl lokale Ollama-Instanzen als auch Cloud-Endpunkte.
- **Continue:** Universell einsetzbar in VS Code und JetBrains; erfordert sorgfältige Pflege der Kontextregeln und `.prompt`-Dateien im Repository.
- **Eclipse Theia:** Ideal für maßgeschneiderte Unternehmens-Entwicklungsumgebungen mit Theia AI; höherer Initialaufwand bei der Systemkonfiguration.
- **avante.nvim:** Schlanker Terminal-Workflow für geübte Neovim-Anwender; erfordert eine funktionierende lokale Lua- und Tree-sitter-Laufzeitumgebung.
