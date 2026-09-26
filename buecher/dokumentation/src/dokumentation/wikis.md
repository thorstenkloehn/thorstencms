# Wikis und Wissensdatenbanken

[Übergeordnete Kategorie: Dokumentenerstellung, Wikis und Notebooks](../dokumentation.md)

Vernetzte Wissenssammlungen mit unterschiedlichen Redaktionsmodellen.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [MediaWiki](https://github.com/wikimedia/mediawiki) | GPL-2.0-or-later | Sehr hoch | Wikimedia-Einsatz und dokumentierter Versionslebenszyklus. | PostgreSQL: [PostgreSQL](https://www.mediawiki.org/wiki/Manual:PostgreSQL/en) |
| 2 | [XWiki](https://www.xwiki.org/xwiki/bin/view/Main/) | LGPL-2.1 | Sehr hoch | Langjährig entwickelte Plattform mit Erweiterungsmodell. | PostgreSQL: [PostgreSQL](https://www.xwiki.org/xwiki/bin/view/Documentation/AdminGuide/Installation/InstallationWAR/InstallationPostgreSQL/) |
| 3 | [DokuWiki](https://github.com/dokuwiki/dokuwiki) | GPL-2.0 | Sehr hoch | Langjährige Entwicklung und dokumentierte Installation. | Dateien: [Textdateien und Medienverzeichnisse](https://github.com/dokuwiki/dokuwiki) |
| 4 | [TiddlyWiki](https://github.com/TiddlyWiki/TiddlyWiki5) | BSD-3-Clause | Hoch | Langjähriges Projekt mit portabler Architektur. | Dateien: [Einzelne HTML-Datei mit eingebetteten Inhalten](https://tiddlywiki.com/dev/static/Data%2520Storage%2520in%2520Single%2520File%2520TiddlyWiki.html) |
| 5 | [Wiki.js](https://js.wiki/about) | AGPL-3.0 | Hoch | Dokumentiertes Wiki mit visueller Bearbeitung und mehreren Speicherintegrationen. | PostgreSQL: [Unterstütztes Datenbank-Backend](https://js.wiki/get-started) |

## Einsatz und Abgrenzung

Wikis dienen in der Dokumentationspraxis häufig als lebendige Nachschlagewerke und Handbücher. Während MediaWiki und XWiki auf relationale Datenbanken setzen, speichert DokuWiki bearbeitbare Textdateien und TiddlyWiki bündelt Wissen in einer portablen HTML-Datei.

- **MediaWiki:** Bewährt für umfangreiche Referenzsammlungen und Enzyklopädien; Vorlagen und Namensräume unterstützen eine konsistente Dokumentationsstruktur.
- **XWiki:** Ermöglicht strukturierte Dokumenttypen und Formulare direkt im Wiki; individuelle Anpassungen erhöhen jedoch den administrativen Pflegeaufwand.
- **DokuWiki:** Schlankes dateibasiertes Dokumentations-Wiki ohne Datenbank; Inhalte liegen direkt als durchsuchbare Textdateien im Verzeichnis.
- **TiddlyWiki:** Eignet sich als kompaktes, eigenständiges Einzeldokument zum Offline-Nachschlagen oder Weitergeben technischer Notizen.
- **Wiki.js:** Modernes Dokumentationsportal mit Mehrbenutzer-Rechtestruktur; für den filterkonformen Betrieb ist PostgreSQL als Backend einzurichten.
