# Kollaborative Arbeitsräume und Docs-as-Code

[Übergeordnete Kategorie: Evolution digitaler Wissenssysteme](../wissenssysteme.md)

Gemeinsame Wissenspflege im Browser oder über versionierte Dateien.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
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

XWiki mit PostgreSQL und das dateibasierte DokuWiki decken Browserredaktion ab. Sphinx und mdBook bearbeiten Inhaltsdateien; Zusammenarbeit erfolgt über einen separaten Review-Prozess.

- **XWiki:** Individuelle Wiki-Anwendungen erhöhen den Betriebsaufwand.
- **Sphinx:** Erweiterungen müssen im Build aufeinander abgestimmt sein.
- **DokuWiki:** Kompatibilität zusätzlicher Plugins gesondert prüfen.
- **mdBook:** Mehrere Produktversionen und komplexe Portale benötigen zusätzliche Organisation.

- **Wiki.js:** Für diese Auswahl PostgreSQL als Anwendungsdatenbank konfigurieren. Zusätzliche Speicherziele sind optional und nicht Bestandteil der gewählten Variante.
