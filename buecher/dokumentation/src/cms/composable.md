# Composable CMS

[Übergeordnete Kategorie: Evolution digitaler Content-Management-Systeme](../cms.md)

CMS-Bausteine für eine aus mehreren Diensten zusammengesetzte Publikationsarchitektur.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
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

Bewertet wird die CMS-Komponente. Die Liste ist keine MACH-Zertifizierung und kein Beleg für eine vollständig integrierte DXP. Suche, Frontend und weitere Dienste müssen abgestimmt werden.

- **Drupal:** Modulabhängigkeiten und größere Upgrades benötigen Planung.
- **Wagtail:** Benötigt für individuelle Inhaltsmodelle ein Django-Entwicklungsteam.
- **Strapi Community Edition:** Enterprise-Code ist ausdrücklich nicht Teil dieser Auswahl.
- **Payload:** Anwendungsentwicklung und Datenmodellierung erforderlich.
- **Keystone:** Entwicklerorientiert; nicht sofort eine fertige Website.

API-Nachweise: [Drupal JSON:API](https://www.drupal.org/docs/core-modules-and-themes/core-modules/jsonapi-module) und [Wagtail API](https://docs.wagtail.org/en/stable/advanced_topics/api/). Strapi wird ausschließlich als [Community Edition](https://github.com/strapi/strapi/blob/develop/LICENSE) bewertet.
