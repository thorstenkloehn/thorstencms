# Mobile Learning und ILT-Präsenzseminare

[Übergeordnete Kategorie: Evolution klassischer Lernmanagement-Systeme](../klassische-lms.md)

Hybride Lernformate mit mobiler Offline-Synchronisation und integrierter Präsenzverwaltung (Instructor-Led Training).

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Kolibri](https://github.com/learningequality/kolibri) | MIT | Hoch | Maßgeschneiderte dateibasierte Plattform für Offline-Lernszenarien und Synchronisation. | Dateien: [Inhaltskanäle und Dateipakete](https://github.com/learningequality/kolibri) |
| 2 | [Moodle](https://github.com/moodle/moodle) | GPL-3.0-or-later | Sehr hoch | Offizielle Moodle App mit Offline-Download und Seminar-/Face-to-Face-Verwaltung. | PostgreSQL: [Offizieller pgsql-Treiber](https://docs.moodle.org/all/de/PostgreSQL) |
| 3 | [BigBlueButton](https://github.com/bigbluebutton/bigbluebutton) | LGPL-3.0 | Sehr hoch | Virtuelle Klassenräume und synchrone Seminarverwaltung für Blended-Learning-Setups. | Dateien: [Aufzeichnungen und Medien im Dateisystem](https://docs.bigbluebutton.org/) |
| 4 | [Canvas LMS](https://github.com/instructure/canvas-lms) | AGPL-3.0 | Sehr hoch | Native Apps für Lernende und Lehrende mit Terminkalender und Abgabemöglichkeiten. | PostgreSQL: [Ausschließlich PostgreSQL](https://github.com/instructure/canvas-lms/wiki/Production-Start) |
| 5 | [Adapt Learning](https://github.com/adaptlearning/adapt_framework) | GPL-3.0 | Hoch | Erstellt vollständig responsive, touch-optimierte Lerninhalte für mobile Browser. | Dateien: [HTML5-/JSON-Dateipakete](https://github.com/adaptlearning/adapt_framework) |

## Einsatz und Abgrenzung

Blended Learning verbindet Vor-Ort-Veranstaltungen mit digitalen Selbstlernphasen.

- **Kolibri:** Ideal für Regionen mit instabiler Netzanbindung; kein synchrones Videokonferenz-Tool.
- **Moodle:** Verwaltet Präsenztermine über Face-to-Face-Plugins; die Mobile-App benötigt konfigurierte Webdienste.
- **BigBlueButton:** Konzentriert sich auf Live-Interaktion; setzt für Kursstrukturen ein übergeordnetes LMS voraus.
- **Canvas LMS:** Gute mobile Bedienbarkeit; Offline-Funktionen sind im Vergleich zu rein dateibasierten Systemen begrenzt.
- **Adapt Learning:** Gestaltet Lernmodule für beliebige Bildschirmgrößen; benötigt ein LMS zur Notenerfassung.
