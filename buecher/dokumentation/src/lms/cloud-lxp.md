# Cloud-native LMS und LXP-Systeme

[Übergeordnete Kategorie: Lernmanagement-Systeme](../klassische-lms.md)

Moderne API-first-Lernplattformen und dezentrale Learning Experience Platforms (LXP).

## Open-Source-Auswahl nach Reifegrad

**3 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Canvas LMS](https://github.com/instructure/canvas-lms) | AGPL-3.0 | Sehr hoch | Kursplattform mit dokumentierten Schnittstellen für eigene Integrationen. | PostgreSQL: [Ausschließlich PostgreSQL](https://github.com/instructure/canvas-lms/wiki/Production-Start) |
| 2 | [H5P](https://github.com/h5p) | MIT | Sehr hoch | Modulare, einbettbare Inhaltskomponenten für Headless- und Portal-Lernszenarien. | Dateien: [Dateibasierte H5P-Pakete (.h5p)](https://h5p.org/documentation) |
| 3 | [Moodle](https://github.com/moodle/moodle) | GPL-3.0-or-later | Sehr hoch | Unterstützt LTI 1.3 Advantage und REST-APIs zur Einbindung in moderne LXP-Ökosysteme. | PostgreSQL: [Offizieller pgsql-Treiber](https://docs.moodle.org/all/de/PostgreSQL) |

## Einsatz und Abgrenzung

Cloud-Betrieb beschreibt die Bereitstellung, eine Learning Experience Platform
(LXP) dagegen einen Schwerpunkt bei der Erschließung und Zusammenstellung von
Lernangeboten. Ein klassisches LMS wird durch Cloud-Hosting nicht automatisch
zur LXP.

Moodle und Canvas können in eine größere Lernumgebung eingebunden werden.
H5P liefert Inhaltsbausteine, aber keine vollständige Plattform. Die konkrete
Verbindung von Anmeldung, Kurszuordnung und Lernfortschritt muss geplant werden.
Die Tabelle bewertet die genannten Kerne; sie ist keine Zusage für fertige
Cloud-Pakete oder externe Dienste.
