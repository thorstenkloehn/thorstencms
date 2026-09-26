# Sprachmodelle in Content-Management-Systemen

[Übergeordnete Kategorie: Integration von Sprachmodellen in Software-Architekturen](../sprachmodell-integration.md)

KI-Integration in redaktionelle Redaktions-Workflows, automatische Übersetzung, Metadaten-Generierung und Barrierefreiheit.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Drupal](https://github.com/drupal/drupal) / [Drupal AI](https://www.drupal.org/project/ai) | GPL-2.0-or-later | Sehr hoch | Offizielles, tief integriertes KI-Subsystem mit austauschbaren Modell-Providern und Vektorsuche. | PostgreSQL: [PostgreSQL als Primärdatenbank](https://www.drupal.org/docs/getting-started/system-requirements/database-server-requirements) |
| 2 | [TYPO3](https://github.com/TYPO3/typo3) | GPL-2.0-or-later | Sehr hoch | Etabliertes Enterprise-CMS mit geprüften KI-Erweiterungen für automatische Übersetzungen und SEO-Metadaten. | PostgreSQL: [PostgreSQL-Unterstützung](https://docs.typo3.org/m/typo3/reference-coreapi/main/en-us/Administration/Installation/SystemRequirements/Index.html) |
| 3 | [Directus](https://github.com/directus/directus) | GPL-3.0 | Hoch | Headless-CMS mit deklarativen KI-Operations zur automatischen Anreicherung relationaler Datensätze. | PostgreSQL: [PostgreSQL als Primärdatenbank](https://docs.directus.io/self-hosted/config-options.html#database) |
| 4 | [Strapi](https://github.com/strapi/strapi) | MIT (Community) | Hoch | Modulares Headless-CMS mit KI-gestützten Redaktions-Plugins für Content-Zusammenfassungen und Tagging. | PostgreSQL: [PostgreSQL-Datenbank-Engine](https://docs.strapi.io/dev-docs/configurations/database) |
| 5 | [Grav](https://github.com/getgrav/grav) | MIT | Hoch | Dateibasiertes Flat-File-CMS mit Markdown-Plugins für assistierte Texterstellung ohne Datenbank-Overhead. | Dateien: [Lokale Markdown- und YAML-Inhalte](https://github.com/getgrav/grav) |

## Einsatz und Abgrenzung

Sprachmodelle unterstützen Redaktionsteams, ersetzen aber nicht das fachliche Freigabe- und Revisionssystem.

- **Drupal AI:** Standardisierte Architektur für In-Editor-Generierung und semantische Suche; erfordert Konfiguration von Provider-API-Schlüsseln.
- **TYPO3:** Ausgezeichnet für mehrsprachige Portale; KI-Übersetzungen müssen vor Veröffentlichung manuell abgenommen werden.
- **Directus:** Nutzt KI-Operationen in Event-Pipelines; relationale Datenmodelle müssen klare Pflichtfelder definieren.
- **Strapi:** Schnelle Headless-Bereitstellung; API-Aufrufe sollten serverseitig gecacht werden, um Modellkosten zu decken.
- **Grav:** Arbeitet vollständig auf Dateien; eignet sich für schlanke Websites mit begrenztem Automatisierungsbedarf.
