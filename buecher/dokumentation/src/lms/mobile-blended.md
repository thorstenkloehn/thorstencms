# Mobile Learning und ILT-Präsenzseminare

[Übergeordnete Kategorie: Lernmanagement-Systeme](../klassische-lms.md)

Hybride Lernformate mit mobiler Offline-Synchronisation und integrierter Präsenzverwaltung (Instructor-Led Training).

## Open-Source-Auswahl nach Reifegrad

**3 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Moodle](https://github.com/moodle/moodle) | GPL-3.0-or-later | Sehr hoch | Kursverwaltung; mobile Nutzung und Präsenzverwaltung gesondert konfigurieren. | PostgreSQL: [Offizieller pgsql-Treiber](https://docs.moodle.org/all/de/PostgreSQL) |
| 2 | [Canvas LMS](https://github.com/instructure/canvas-lms) | AGPL-3.0 | Sehr hoch | Native Apps für Lernende und Lehrende mit Terminkalender und Abgabemöglichkeiten. | PostgreSQL: [Ausschließlich PostgreSQL](https://github.com/instructure/canvas-lms/wiki/Production-Start) |
| 3 | [Adapt Learning](https://github.com/adaptlearning/adapt_framework) | GPL-3.0 | Hoch | Erstellt vollständig responsive, touch-optimierte Lerninhalte für mobile Browser. | Dateien: [HTML5-/JSON-Dateipakete](https://github.com/adaptlearning/adapt_framework) |

## Einsatz und Abgrenzung

Blended Learning kombiniert Präsenzveranstaltungen mit digitalen Lernphasen.
Moodle und Canvas können die Kursorganisation übernehmen. Adapt erstellt
Lerninhalte für die Auslieferung im Browser; es ersetzt kein LMS.

Präsenztermine, Teilnahmenachweise und Offline-Funktionen hängen von der
gewählten Konfiguration und gegebenenfalls zusätzlichen Erweiterungen ab.
Ein brauchbares Beispiel verbindet eine vorbereitende Leseaufgabe, einen
Termin vor Ort und eine anschließende Aufgabe mit Rückmeldung.
