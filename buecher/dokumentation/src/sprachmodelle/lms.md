# Sprachmodelle in Lernmanagement-Systemen

[Übergeordnete Kategorie: Integration von Sprachmodellen in Software-Architekturen](../sprachmodell-integration.md)

KI-gestützte Tutoren, adaptive Lernpfade, automatische Fragen-Generierung und didaktisches Feedback.

## Open-Source-Auswahl nach Reifegrad

**3 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Moodle](https://github.com/moodle/moodle) | GPL-3.0-or-later | Sehr hoch | Offizielles modulares KI-Subsystem mit Provider-Plugins für Zusammenfassungen und Textgenerierung. | PostgreSQL: [Offizieller pgsql-Treiber](https://docs.moodle.org/all/de/PostgreSQL) |
| 2 | [Canvas LMS](https://github.com/instructure/canvas-lms) | AGPL-3.0 | Sehr hoch | LMS-Kern für die Anbindung externer Lernwerkzeuge; KI-Dienst separat auswählen. | PostgreSQL: [Ausschließlich PostgreSQL](https://github.com/instructure/canvas-lms/wiki/Production-Start) |
| 3 | [H5P](https://github.com/h5p) | MIT | Sehr hoch | Interaktive Lerninhalte; keine pauschale Zusage für integrierte KI-Erstellung. | Dateien: [Dateibasierte H5P-Pakete (.h5p)](https://h5p.org/documentation) |

## Einsatz und Abgrenzung

Moodle dokumentiert ein [KI-Subsystem](https://docs.moodle.org/en/AI_subsystem).
Die Verfügbarkeit einzelner Aktionen hängt von Moodle-Version, Anbieter und
Konfiguration ab. Die Bewertung in der Tabelle gilt für den LMS-Kern.

Canvas wird als Plattform für die Anbindung externer Werkzeuge betrachtet.
H5P ist ein Inhaltsformat und Werkzeugbestand für Übungen. Für beide wird
hier keine pauschale integrierte KI-Tutorfunktion behauptet.

Vor dem Einsatz einer KI-Anbindung sind übermittelte Lerndaten, Zugriffsrechte,
Transparenz und fachliche Rückmeldungen zu prüfen. Ein möglicher Einstieg ist
ein Entwurf für eine Übungsfrage, den die Lehrperson vor der Verwendung
bearbeitet. Automatische Benotung wird damit nicht empfohlen.
