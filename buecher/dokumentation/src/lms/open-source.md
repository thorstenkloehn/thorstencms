# Open-Source-LMS und Konsortialplattformen

[Übergeordnete Kategorie: Evolution klassischer Lernmanagement-Systeme](../klassische-lms.md)

Gemeinschaftlich entwickelte Plattformen mit modularen Plugin-Architekturen und akademischer Trägerschaft.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Moodle](https://github.com/moodle/moodle) | GPL-3.0-or-later | Sehr hoch | Größte weltweite Open-Source-Gemeinschaft mit Tausenden Community-Plugins. | PostgreSQL: [Offizieller pgsql-Treiber](https://docs.moodle.org/all/de/PostgreSQL) |
| 2 | [Canvas LMS](https://github.com/instructure/canvas-lms) | AGPL-3.0 | Sehr hoch | Open-Source-Kern der im Hochschulbereich führenden Cloud-Plattform. | PostgreSQL: [Ausschließlich PostgreSQL](https://github.com/instructure/canvas-lms/wiki/Production-Start) |
| 3 | [Open edX](https://github.com/openedx/edx-platform) | AGPL-3.0 | Hoch | Ursprünglich von MIT und Harvard gegründete Plattform für weltweite Online-Bildung. | PostgreSQL: [Django-Backend für Core-Services](https://github.com/openedx/edx-platform) |
| 4 | [Sakai](https://github.com/sakaiproject/sakai) | ECL-2.0 | Hoch | Konsortial-Plattform führender internationaler Universitäten seit 2004. | PostgreSQL: [Unterstützte relationale Datenbank](https://sakaiproject.atlassian.net/wiki/spaces/DOC/pages/38043653/Database+Configuration) |
| 5 | [Frappe LMS](https://github.com/frappe/lms) | AGPL-3.0 | Hoch | Modernes, modulare Open-Source-LMS auf Python- und Frappe-Basis. | PostgreSQL: [PostgreSQL-Unterstützung via Frappe-Backend](https://github.com/frappe/lms) |

## Einsatz und Abgrenzung

Open-Source-Systeme sichern Datenhoheit und Unabhängigkeit von kommerziellen Lizenzmodellen.

- **Moodle:** Höchste Anpassbarkeit durch Plugins; Konfigurationsaufwand und Pflegeaufwand steigen mit der Zahl der Erweiterungen.
- **Canvas LMS:** Moderne Benutzeroberfläche; Trennung zwischen Open-Source-Code und proprietären Cloud-Diensten des Herstellers beachten.
- **Open edX:** Ideal für strukturierte Großkurse; erfordert erfahrene Systemadministration für Microservices.
- **Sakai:** Enterprise-Java-Architektur; erfordert JVM-Expertise im Rechenzentrum.
- **Frappe LMS:** Schlanker und moderner als traditionelle Web-LMS; geringere Feature-Dichte als Moodle.
