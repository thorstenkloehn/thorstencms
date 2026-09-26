# Kollaborative Arbeitsräume und Docs-as-Code

[Übergeordnete Kategorie: Digitale Wissenssysteme](../wissenssysteme.md)

Gemeinsame Wissenspflege im Browser oder über versionierte Dateien.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [XWiki](https://www.xwiki.org/xwiki/bin/view/Main/) | LGPL-2.1 | Sehr hoch | Langjährig entwickelte Plattform mit Erweiterungsmodell. | PostgreSQL: [PostgreSQL](https://www.xwiki.org/xwiki/bin/view/Documentation/AdminGuide/Installation/InstallationWAR/InstallationPostgreSQL/) |
| 2 | [Sphinx](https://github.com/sphinx-doc/sphinx) | BSD-2-Clause | Sehr hoch | Umfangreiches Handbuch und ausgebautes Erweiterungssystem. | Dateien: [reStructuredText-/Markdown-Quellen und HTML-Dateien](https://github.com/sphinx-doc/sphinx) |
| 3 | [DokuWiki](https://github.com/dokuwiki/dokuwiki) | GPL-2.0 | Sehr hoch | Langjährige Entwicklung und dokumentierte Installation. | Dateien: [Textdateien und Medienverzeichnisse](https://github.com/dokuwiki/dokuwiki) |
| 4 | [mdBook](https://github.com/rust-lang/mdBook) | MPL-2.0 | Hoch | Fokussierter Generator mit Benutzerhandbuch. | Dateien: [Markdown- und HTML-Dateien](https://github.com/rust-lang/mdBook) |
| 5 | [Wiki.js](https://js.wiki/about) | AGPL-3.0 | Hoch | Dokumentiertes Wiki mit visueller Bearbeitung und mehreren Speicherintegrationen. | PostgreSQL: [Unterstütztes Datenbank-Backend](https://js.wiki/get-started) |

## Einsatz und Abgrenzung

Kollaborative Arbeitsräume verbinden gemeinsame Bearbeitung im Browser mit versionierten Datei- und Codebeständen. Berechtigungen, Review-Prozesse und Speicherstrukturen müssen zum Arbeitsalltag des Teams passen.

- **XWiki:** Dient als zentraler Enterprise-Arbeitsraum mit differenzierten Benutzerrechten und formulargestützten Workflows im Browser.
- **Sphinx:** Verlagert Arbeitsräume in Code-Repositories; Dokumentation wird im Team dezentral über Git und Pull Requests gepflegt.
- **DokuWiki:** Bietet unkomplizierte Team-Arbeitsbereiche über Namensräume, ohne separaten Datenbankbetrieb zu erfordern.
- **mdBook:** Schlanker, fokussierter Handbuch-Arbeitsraum für Software- und Entwicklungsteams mit klar gegliederter Kapitelführung.
- **Wiki.js:** Kombiniert grafische Team-Arbeitsbereiche mit optionalem bidirektionalem Git-Speicherabgleich; für die relationale Datenhaltung ist PostgreSQL zu konfigurieren.
