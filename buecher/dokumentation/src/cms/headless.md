# Headless und Decoupled CMS

[Übergeordnete Kategorie: Content-Management-Systeme](../cms.md)

Inhaltspflege getrennt von Darstellung und Auslieferung.

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

Headless-Architekturen trennen die Inhaltspflege strikt von der Präsentationsschicht. Redaktionelle Vorschau, Session-Handling und Cache-Invalidierung für externe Frontends müssen separat im Projekt gelöst werden.

- **Drupal:** Dient über das Kernmodul [JSON:API](https://www.drupal.org/docs/core-modules-and-themes/core-modules/jsonapi-module) als entkoppeltes Backend; Vorschaumechanismen für separate Frontends verlangen zusätzlichen Integrationsaufwand.
- **Wagtail:** Stellt Inhaltsbäume über die offizielle [Wagtail API](https://docs.wagtail.org/en/stable/advanced_topics/api/) bereit; Redaktionsansichten und Benutzer-Frontends bleiben technologisch getrennt.
- **Strapi Community Edition:** Natives API-first-CMS mit anpassbaren REST- und GraphQL-Endpunkten; Enterprise-Features sind ausdrücklich nicht Teil der [freien Lizenz](https://github.com/strapi/strapi/blob/develop/LICENSE).
- **Payload:** TypeScript-basiertes Headless-CMS mit enger Anbindung an moderne Frontend-Frameworks und flexiblen Zugriffskontrollen.
- **Keystone:** Generiert aus deklarativen TypeScript-Schemas eine performante GraphQL-API für individuell entwickelte Frontends.
