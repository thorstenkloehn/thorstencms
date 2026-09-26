# SCORM- und Interoperabilitätsstandards

[Übergeordnete Kategorie: Evolution klassischer Lernmanagement-Systeme](../klassische-lms.md)

Paketierte Lerninhalte, Autorenwerkzeuge und Learning Record Stores nach AICC, SCORM und xAPI.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Moodle](https://github.com/moodle/moodle) | GPL-3.0-or-later | Sehr hoch | Vollständige native Laufzeit-Engine für SCORM 1.2 und AICC. | PostgreSQL: [Offizieller pgsql-Treiber](https://docs.moodle.org/all/de/PostgreSQL) |
| 2 | [H5P](https://github.com/h5p) | MIT | Sehr hoch | Offener Standard für interaktive, dateibasierte HTML5-Lernpakete. | Dateien: [Dateibasierte H5P-Pakete (.h5p Zip-Format)](https://h5p.org/documentation) |
| 3 | [Adapt Learning](https://github.com/adaptlearning/adapt_framework) | GPL-3.0 | Hoch | Framework zur Erstellung responsiver, SCORM-konformer Lernmodule. | Dateien: [JSON-/HTML5-basierte Ausgabepakete](https://github.com/adaptlearning/adapt_framework) |
| 4 | [Ralph LRS](https://github.com/openfun/ralph) | MIT | Hoch | Moderner Learning Record Store für xAPI- und LTI-Events. | PostgreSQL: [Dokumentierter PostgreSQL-Speicherweg](https://github.com/openfun/ralph) |
| 5 | [TRAX LRS](https://github.com/trax-project/trax-lrs) | GPL-3.0 | Hoch | Etablierter xAPI-LRS mit nativer PostgreSQL-Datenbankanbindung. | PostgreSQL: [PostgreSQL-Konfiguration via Laravel](https://trax-lrs.com/docs/) |

## Einsatz und Abgrenzung

Interoperabilitätsstandards trennen Lerninhalte von der ausliefernden Plattform.

- **Moodle:** Dient als zertifizierter SCORM-Host; komplexe Verzweigungen nach SCORM 2004 4th Edition benötigen separate Plugins.
- **H5P:** Ermöglicht interaktive Übungen direkt im Web; Notenübermittlung erfordert eine LMS-Anbindung (z. B. via LTI oder Plugin).
- **Adapt Learning:** Autorentool für moderne SCORM-Pakete; benötigt ein separates LMS zur Bereitstellung und Auswertung.
- **Ralph LRS:** Speichert xAPI-Statements unabhängig vom LMS; Auswertungs-Dashboards müssen separat ergänzt werden.
- **TRAX LRS:** Konzentriert sich auf xAPI-Datenspeicherung und Validierung; kein vollwertiges Kursverwaltungssystem.
