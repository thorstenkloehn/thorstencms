# SCORM- und Interoperabilitätsstandards

[Übergeordnete Kategorie: Lernmanagement-Systeme](../klassische-lms.md)

Paketierte Lerninhalte, Autorenwerkzeuge und Learning Record Stores nach AICC, SCORM und xAPI.

## Open-Source-Auswahl nach Reifegrad

**3 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Moodle](https://github.com/moodle/moodle) | GPL-3.0-or-later | Sehr hoch | Dokumentierte Unterstützung für SCORM 1.2 im Standardmodul. | PostgreSQL: [Offizieller pgsql-Treiber](https://docs.moodle.org/all/de/PostgreSQL) |
| 2 | [H5P](https://github.com/h5p) | MIT | Sehr hoch | Offener Standard für interaktive, dateibasierte HTML5-Lernpakete. | Dateien: [Dateibasierte H5P-Pakete (.h5p Zip-Format)](https://h5p.org/documentation) |
| 3 | [Adapt Learning](https://github.com/adaptlearning/adapt_framework) | GPL-3.0 | Hoch | Framework zur Erstellung responsiver, SCORM-konformer Lernmodule. | Dateien: [JSON-/HTML5-basierte Ausgabepakete](https://github.com/adaptlearning/adapt_framework) |

## Einsatz und Abgrenzung

Moodle, H5P und Adapt übernehmen unterschiedliche Aufgaben: Moodle verwaltet
Kurse, H5P stellt interaktive Inhalte bereit und Adapt dient der Erstellung
von Lernmodulen. Paketdateien enthalten keine vollständige Benutzer- und
Notenverwaltung.

Bei Moodle ist SCORM 1.2 dokumentiert; das Standardmodul bietet keine vollständige
SCORM-2004-Unterstützung. Eine generelle Zertifizierungszusage wird hier nicht
gegeben. [Moodle: SCORM FAQ](https://docs.moodle.org/en/SCORM_FAQ).

Zum Prüfen eines Lernpakets gehören Start, Abschlussmeldung, erneuter Aufruf
und Übernahme der Ergebnisse. Dafür muss die tatsächliche Kombination aus
Paket und Zielplattform getestet werden.
