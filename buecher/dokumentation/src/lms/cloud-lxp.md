# Cloud-native LMS und LXP-Systeme

[Übergeordnete Kategorie: Evolution klassischer Lernmanagement-Systeme](../klassische-lms.md)

Moderne API-first-Lernplattformen und dezentrale Learning Experience Platforms (LXP).

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Canvas LMS](https://github.com/instructure/canvas-lms) | AGPL-3.0 | Sehr hoch | Moderne Cloud-native API-first-Architektur mit modularer Service-Struktur. | PostgreSQL: [Ausschließlich PostgreSQL](https://github.com/instructure/canvas-lms/wiki/Production-Start) |
| 2 | [Open edX](https://github.com/openedx/edx-platform) | AGPL-3.0 | Hoch | Skalierbare Microservice-Architektur für massive Online-Kurse und dezentrale Portale. | PostgreSQL: [Django-Backend für Core-Services](https://github.com/openedx/edx-platform) |
| 3 | [Frappe LMS](https://github.com/frappe/lms) | AGPL-3.0 | Hoch | Schlankes, modernes Single-Page-LMS mit integrierter Kurs- und Community-Erfahrung. | PostgreSQL: [PostgreSQL via Frappe-Backend](https://github.com/frappe/lms) |
| 4 | [H5P](https://github.com/h5p) | MIT | Sehr hoch | Modulare, einbettbare Inhaltskomponenten für Headless- und Portal-Lernszenarien. | Dateien: [Dateibasierte H5P-Pakete (.h5p)](https://h5p.org/documentation) |
| 5 | [Moodle](https://github.com/moodle/moodle) | GPL-3.0-or-later | Sehr hoch | Unterstützt LTI 1.3 Advantage und REST-APIs zur Einbindung in moderne LXP-Ökosysteme. | PostgreSQL: [Offizieller pgsql-Treiber](https://docs.moodle.org/all/de/PostgreSQL) |

## Einsatz und Abgrenzung

LXPs stellen selbstbestimmtes Lernen, Content-Kuration und API-Kopplung vor starre Lehrpläne.

- **Canvas LMS:** Vorreiter bei offenen APIs und LTI-Integration; hoher Infrastrukturaufwand für Eigenbetrieb.
- **Open edX:** Bietet modulare Micro-Frontends (MFE); setzt Docker-/Kubernetes-Betrieb (Tutor) voraus.
- **Frappe LMS:** Schneller Einstieg und gute UX; erfordert das Frappe-Ökosystem.
- **H5P:** Ermöglicht interaktive Bausteine ohne Systembindung; übernimmt selbst kein Kurs- oder Nutzermanagement.
- **Moodle:** Kann als Content- und LTI-Provider in modernen Portalen agieren; bleibt im Kern ein klassisches LMS.
