# Klassische CMS

[Übergeordnete Kategorie: Content-Management-Systeme](../cms.md)

Redaktion, Inhaltsverwaltung und Veröffentlichung in einer Plattform.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Drupal](https://www.drupal.org/project/drupal/releases) | GPL-2.0-or-later | Sehr hoch | Geregelte Core-Releases und umfangreiche Dokumentation. | PostgreSQL: [PostgreSQL](https://www.drupal.org/docs/getting-started/system-requirements/database-server-requirements) |
| 2 | [TYPO3](https://github.com/TYPO3/typo3) | GPL-2.0-or-later | Sehr hoch | Etabliertes Core-Team und Betriebsdokumentation. | PostgreSQL: [PostgreSQL](https://docs.typo3.org/m/typo3/reference-coreapi/main/en-us/Administration/Installation/SystemRequirements/Index.html) |
| 3 | [Joomla](https://github.com/joomla/joomla-cms) | GPL-2.0-or-later | Sehr hoch | Langjährige Entwicklung und veröffentlichte Versionshistorie. | PostgreSQL: [PostgreSQL](https://manual.joomla.org/docs/next/get-started/technical-requirements/) |
| 4 | [Wagtail](https://github.com/wagtail/wagtail) | BSD-3-Clause | Hoch | Dokumentiertes Django-CMS mit Community und Support. | PostgreSQL: [PostgreSQL](https://docs.wagtail.org/en/stable-7.4.x/releases/upgrading.html) |
| 5 | [Grav](https://github.com/getgrav/grav) | MIT | Hoch | Dokumentiertes PHP-System mit Markdown und Templates. | Dateien: [Markdown-, YAML- und Mediendateien](https://github.com/getgrav/grav) |

## Einsatz und Abgrenzung

Die Bewertung gilt für den Kern. Plugins, Templates und das konkrete Betriebskonzept können die Gesamtreife deutlich verändern.

- **Drupal:** Modulabhängigkeiten und größere Upgrades benötigen Planung.
- **TYPO3:** Einrichtung und projektspezifische Anpassungen verlangen Fachkenntnisse.
- **Joomla:** Erweiterungen müssen zur eingesetzten Hauptversion passen.
- **Wagtail:** Benötigt für individuelle Inhaltsmodelle ein Django-Entwicklungsteam.

- **Grav:** Zeigt, dass ein vollwertiges Redaktionserlebnis samt Administrations-Backend auch ohne relationale Datenbank möglich ist; Seiten und Konfigurationen werden direkt in Twig-Templates, YAML und Markdown strukturiert.
