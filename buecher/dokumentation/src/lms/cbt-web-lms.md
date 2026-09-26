# CBT-Pioniere und frühe Web-LMS

[Übergeordnete Kategorie: Evolution klassischer Lernmanagement-Systeme](../klassische-lms.md)

Frühe rechnergestützte Lernprogramme und monolithische Web-Kursräume der ersten Generation.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Moodle](https://github.com/moodle/moodle) | GPL-3.0-or-later | Sehr hoch | Etablierter weltweiter Standard für Kurs- und Modulräume. | PostgreSQL: [Offizieller pgsql-Treiber](https://docs.moodle.org/all/de/PostgreSQL) |
| 2 | [Canvas LMS](https://github.com/instructure/canvas-lms) | AGPL-3.0 | Sehr hoch | Bewährte Kursraum- und Semesterverwaltung im Hochschulbereich. | PostgreSQL: [Ausschließlich PostgreSQL](https://github.com/instructure/canvas-lms/wiki/Production-Start) |
| 3 | [Sakai](https://github.com/sakaiproject/sakai) | ECL-2.0 | Hoch | Hochschulkonsortium für strukturierte Semesterkursräume. | PostgreSQL: [Relationale Datenbank-Konfiguration](https://sakaiproject.atlassian.net/wiki/spaces/DOC/pages/38043653/Database+Configuration) |
| 4 | [Opigno LMS](https://www.drupal.org/project/opigno_lms) | GPL-2.0-or-later | Hoch | Vollwertiges Kurs-LMS auf modularer Drupal-Basis. | PostgreSQL: [PostgreSQL via Drupal-Kern](https://www.drupal.org/docs/getting-started/system-requirements/database-server-requirements) |
| 5 | [Kolibri](https://github.com/learningequality/kolibri) | MIT | Hoch | Strukturierte lineare Lehrgänge für lokale und dateibasierte Umgebungen. | Dateien: [Inhaltskanäle und Dateipakete](https://github.com/learningequality/kolibri) |

## Einsatz und Abgrenzung

Klassische Web-LMS digitalisieren traditionelle Vorlesungs- und Seminarstrukturen mit Kurslisten, Aufgabenabgaben und Foren.

- **Moodle:** Monolithische Architektur; Versionsupgrades erfordern sorgfältige Plugin-Prüfung.
- **Canvas LMS:** Umfangreicher Ruby-on-Rails-Stack; Self-Hosting verlangt solide DevOps-Erfahrung.
- **Sakai:** Java-basierter Serverbetrieb über Apache Tomcat; im deutschsprachigen Raum kleinere Betreiberbasis.
- **Opigno LMS:** Basiert auf Drupal; profitiert von Drupals Sicherheitsmodell, erfordert aber Drupal-Fachkenntnisse.
- **Kolibri:** Konzipiert für synchrone und asynchrone Offline-Lehre; kein Campus-Prüfungssystem.
