# Redaktions- und Content-Clients

[Übergeordnete Kategorie: Mobile und Desktop-Apps in Content- und Wissenssystemen](../mobile-desktop-apps.md)

Mobile und Desktop-Anwendungen zur Inhaltsverwaltung, Medienaufnahme und Veröffentlichung.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [WordPress Mobile](https://github.com/wordpress-mobile/WordPress-Android) | GPL-2.0-or-later | Sehr hoch | Ausgereifte mobile Redaktions-App für Entwürfe, Freigaben und Kamera-Upload. | Dateien: [Lokaler Medien-Cache und REST-API-Synchronisation](https://github.com/wordpress-mobile/WordPress-Android) |
| 2 | [Ghost Desktop](https://github.com/TryGhost/Ghost-Desktop) | MIT | Hoch | Offizieller Desktop-Client für Autoren mit Multi-Blog-Verwaltung und Offline-Entwürfen. | Dateien: [Lokaler Markdown-Cache und API-Abgleich](https://github.com/TryGhost/Ghost-Desktop) |
| 3 | [Decap CMS](https://github.com/decaporg/decap-cms) | MIT | Hoch | Git-basierter Single-Page-Client für dateibasierte Redaktionsworkflows. | Dateien: [Markdown-, YAML- und JSON-Dateien im Git-Repo](https://decapcms.org/) |
| 4 | [Front Matter CMS](https://github.com/estruyf/vscode-front-matter) | MIT | Hoch | Desktop-Redaktionsumgebung für statische Webseiten und Headless-Inhalte. | Dateien: [Markdown-Dateien mit Frontmatter im Workspace](https://frontmatter.codes/) |
| 5 | [Directus App](https://github.com/directus/directus) | GPL-3.0 | Hoch | Responsive Web- und App-Oberfläche für strukturierte Datenverwaltung auf PostgreSQL. | PostgreSQL: [PostgreSQL als Primärdatenbank](https://docs.directus.io/self-hosted/config-options.html#database) |

## Einsatz und Abgrenzung

Spezialisierte Clients entkoppeln Redaktionsaufgaben von der primären Web-Admin-Oberfläche.

- **WordPress Mobile:** Ermöglicht Veröffentlichungen und Medien-Uploads von unterwegs; setzt XML-RPC oder REST-API voraus.
- **Ghost Desktop:** Bietet ungestörtes Schreiben auf dem Desktop; Offline-Entwürfe müssen vor dem Veröffentlichen synchronisiert werden.
- **Decap CMS:** Arbeitet direkt auf Git-Repositories; ideal für Static-Site-Generatoren wie Hugo oder Astro.
- **Front Matter CMS:** Integriert in VS Code; richtet sich an Entwickler und technische Redakteure.
- **Directus App:** Universelles Headless-Daten-Dashboard; relationale Tabellenstruktur erfordert Schema-Planung.
