# Wiki-Systeme

[Übergeordnete Kategorie: Digitale Wissenssysteme](../wissenssysteme.md)

Gemeinsam gepflegte Seiten mit Verweisen und Versionierung.

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

Wiki-Systeme bilden das Rückgrat offener Wissensvernetzung. Die Systeme unterscheiden sich grundlegend in ihrer Architektur: MediaWiki, XWiki und Wiki.js setzen auf relationale Datenbanken (hier PostgreSQL), während DokuWiki und TiddlyWiki dateibasiert ohne Datenbank auskommen.

- **MediaWiki:** Etablierter Maßstab für großflächige, hierarchiefreie Wissensnetze; LTS-Releases und Schema-Migrationen erfordern eine vorausschauende Betriebsplanung.
- **XWiki:** Leistungsfähige Plattform für semantisch strukturiertes Wissensmanagement mit eigenem Makro- und Applikationsbaukasten.
- **DokuWiki:** Ausgezeichnet geeignet für wartungsarme Wissenssammlungen im Dateisystem; Textdateien ermöglichen einfache Backups und direkte Versionierung.
- **TiddlyWiki:** Nicht-lineares, modulares persönliches Wissenssystem; für verteilte Teams sind geeignete Synchronisations-Gateways erforderlich.
- **Wiki.js:** Universelle Wissensplattform mit moderner Weboberfläche; der filterkonforme Betrieb setzt die explizite Konfiguration von PostgreSQL als Primärdatenbank voraus.
