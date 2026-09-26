# Redaktions- und Content-Clients

[Übergeordnete Kategorie: Mobile und Desktop-Apps in Content- und Wissenssystemen](../mobile-desktop-apps.md)

Mobile und Desktop-Anwendungen zur Inhaltsverwaltung, Medienaufnahme und Veröffentlichung.

## Open-Source-Auswahl nach Reifegrad

**2 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Decap CMS](https://github.com/decaporg/decap-cms) | MIT | Hoch | Git-basierter Single-Page-Client für dateibasierte Redaktionsworkflows. | Dateien: [Markdown-, YAML- und JSON-Dateien im Git-Repo](https://decapcms.org/) |
| 2 | [Front Matter CMS](https://github.com/estruyf/vscode-front-matter) | MIT | Hoch | Desktop-Redaktionsumgebung für statische Webseiten und Headless-Inhalte. | Dateien: [Markdown-Dateien mit Frontmatter im Workspace](https://frontmatter.codes/) |

## Einsatz und Abgrenzung

Decap CMS und Front Matter CMS bearbeiten Inhaltsdateien im Umfeld eines
Git-Repositories beziehungsweise eines lokalen Projekts. Die Auswahl umfasst
damit eine Browseroberfläche und eine Editor-Erweiterung, nicht zwei native
Smartphone-Apps.

Beispiel: Eine Redaktion ändert Titel und Termin einer Inhaltsdatei. Nach der
Prüfung erzeugt der Site-Generator die Website. Vorschau, Rechte und
Veröffentlichung werden im Projekt eingerichtet.

Ein Medien-Cache oder ein API-Client für ein fremdes CMS genügt dem Speicherfilter
nicht. Deshalb werden die bisherigen WordPress- und Ghost-Clients hier nicht
weiter als dateibasierte Gesamtvarianten empfohlen.
