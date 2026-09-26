# Composable CMS

[Übergeordnete Kategorie: Content-Management-Systeme](../cms.md)

CMS-Bausteine für eine aus mehreren Diensten zusammengesetzte Publikationsarchitektur.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Drupal](https://www.drupal.org/project/drupal/releases) | GPL-2.0-or-later | Sehr hoch | Geregelte Core-Releases und umfangreiche Dokumentation. | PostgreSQL: [PostgreSQL](https://www.drupal.org/docs/getting-started/system-requirements/database-server-requirements) |
| 2 | [Wagtail](https://github.com/wagtail/wagtail) | BSD-3-Clause | Hoch | Dokumentiertes Django-CMS mit Community und Support. | PostgreSQL: [PostgreSQL](https://docs.wagtail.org/en/stable-7.4.x/releases/upgrading.html) |
| 3 | [Strapi Community Edition](https://github.com/strapi/strapi) | MIT (Community) | Hoch | Dokumentiertes API-CMS mit Tests und Entwicklungshistorie. | PostgreSQL: [PostgreSQL; explizit konfigurieren](https://docs.strapi.io/cms/configurations/database) |
| 4 | [Payload](https://github.com/payloadcms/payload) | MIT | Hoch | Dokumentiertes TypeScript-CMS mit Sicherheitsrichtlinie. | PostgreSQL: [PostgreSQL mit db-postgres](https://payloadcms.com/docs/database/postgres) |
| 5 | [Keystone](https://github.com/keystonejs/keystone) | MIT | Hoch | Dokumentiertes Schema-, GraphQL- und Administrationsmodell. | PostgreSQL: [PostgreSQL](https://keystonejs.com/docs/config/config/) |

## Einsatz und Abgrenzung

In Composable-Architekturen fungiert das CMS als modularer Inhaltsbaustein neben eigenständigen E-Commerce-, Such- und Lokalisierungsdiensten. Die Integration verlangt saubere Schnittstellen und Orchestrierung.

- **Drupal:** Dient als robuster Content-Hub für Multichannel-Ausspielungen; verlangt eine klare Definition der Service-Grenzen gegenüber Drittsystemen.
- **Wagtail:** Lässt sich über APIs hervorragend mit externen Diensten und Microservices verbinden, erfordert jedoch Entwicklungsressourcen für benutzerdefinierte Konnektoren.
- **Strapi Community Edition:** Leichtgewichtiger Baustein für modulare Webhook- und API-Architekturen; die quelloffene Version verzichtet auf proprietäre Enterprise-Erweiterungen.
- **Payload:** Lässt sich dank TypeScript-Codebasis nahtlos in modulare Full-Stack-Landschaften einbetten und mit maßgeschneiderter Geschäftslogik erweitern.
- **Keystone:** Schema-first-Ansatz zur Modellierung domänenspezifischer Datenbausteine innerhalb vernetzter Microservice-Umgebungen.
