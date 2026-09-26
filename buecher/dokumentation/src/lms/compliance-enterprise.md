# Compliance, Pflichtschulungen und Talent-Suiten

[Übergeordnete Kategorie: Evolution klassischer Lernmanagement-Systeme](../klassische-lms.md)

Lösungen für auditierbare Nachweise, regulatorische Pflichtunterweisungen und Zertifizierungszyklen.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Moodle](https://github.com/moodle/moodle) | GPL-3.0-or-later | Sehr hoch | Etablierte Workplace- und Rezertifizierungs-Erweiterungen für regelmäßige Pflichtschulungen. | PostgreSQL: [Offizieller pgsql-Treiber](https://docs.moodle.org/all/de/PostgreSQL) |
| 2 | [Opigno LMS](https://www.drupal.org/project/opigno_lms) | GPL-2.0-or-later | Hoch | Spezialisiert auf Unternehmensschulungen, Berechtigungspfade und Zertifikatsmanagement. | PostgreSQL: [PostgreSQL via Drupal](https://www.drupal.org/docs/getting-started/system-requirements/database-server-requirements) |
| 3 | [Canvas LMS](https://github.com/instructure/canvas-lms) | AGPL-3.0 | Sehr hoch | Revisionssichere Bewertungs- und Protokollierungsstrukturen im Kern. | PostgreSQL: [Ausschließlich PostgreSQL](https://github.com/instructure/canvas-lms/wiki/Production-Start) |
| 4 | [Open edX](https://github.com/openedx/edx-platform) | AGPL-3.0 | Hoch | Strukturierte Verifizierungsprozesse für offizielle Zertifikate und Nachweise. | PostgreSQL: [Django-Backend für Core-Services](https://github.com/openedx/edx-platform) |
| 5 | [Ralph LRS](https://github.com/openfun/ralph) | MIT | Hoch | Auditierbare Erfassung von Schulungsnachweisen über standardisierte xAPI-Abläufe. | PostgreSQL: [Dokumentierter PostgreSQL-Speicherweg](https://github.com/openfun/ralph) |

## Einsatz und Abgrenzung

Compliance-Systeme verlangen unveränderbare Audit-Trails und geregelte Rezertifizierungsintervalle.

- **Moodle:** Standard-Workplace-Funktionen erfordern passende Plugins oder Konfiguration für Fristenüberwachung.
- **Opigno LMS:** Ermöglicht komplexe Trainingspläne nach Organisationseinheiten; benötigt Drupal-Wartung.
- **Canvas LMS:** Ausgezeichnet für Noten und Fristen; Verknüpfung mit HRIS-Systemen muss separat eingerichtet werden.
- **Open edX:** Bietet robuste Prüfungsaufsicht (Proctoring-Integrationen); aufwendig im Setup für reine Pflichtunterweisungen.
- **Ralph LRS:** Sammelt rechtssichere Lernaktivitätsdaten; die fachliche Beurteilung erfolgt im nachgelagerten System.
