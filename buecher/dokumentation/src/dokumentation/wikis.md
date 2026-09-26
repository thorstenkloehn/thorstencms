# Wikis und Wissensdatenbanken

[Übergeordnete Kategorie: Dokumentenerstellung, Wikis und Notebooks](../dokumentation.md)

Vernetzte Wissenssammlungen mit unterschiedlichen Redaktionsmodellen.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
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

MediaWiki und XWiki bleiben für PostgreSQL-Betrieb enthalten. DokuWiki speichert Textdateien; TiddlyWiki kann sein gesamtes Wiki in einer HTML-Datei halten.

- **MediaWiki:** Erweiterungen und Upgrades müssen gemeinsam geplant werden.
- **XWiki:** Individuelle Wiki-Anwendungen erhöhen den Betriebsaufwand.
- **DokuWiki:** Kompatibilität zusätzlicher Plugins gesondert prüfen.
- **TiddlyWiki:** Gemeinsame Bearbeitung und Synchronisierung brauchen ein passendes Betriebskonzept.

- **Wiki.js:** Für diese Auswahl PostgreSQL als Anwendungsdatenbank konfigurieren. Zusätzliche Speicherziele sind optional und nicht Bestandteil der gewählten Variante.
