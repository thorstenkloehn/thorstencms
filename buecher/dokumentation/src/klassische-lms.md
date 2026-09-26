# Lernmanagement-Systeme: Kurse, Aktivitäten und Lernfortschritt

Ein Lernmanagement-System verbindet Kursmaterialien mit Teilnehmenden,
Aufgaben und Rückmeldungen. Es hilft beispielsweise dabei, einen Kurs
freizuschalten, eine Abgabe einzusammeln und eine Bewertung mitzuteilen.
Welche Nachweise daraus entstehen, hängt von Kursgestaltung und Betrieb ab.

## Beispiel: Eine interne Schulung

Die Kursleitung ordnet Lernende einer Schulung zu und setzt eine Frist.
Nach der Bearbeitung werden Testergebnisse gespeichert. Für einen belastbaren
Teilnahmenachweis müssen zusätzlich Identität, Bewertungsregeln, Aufbewahrung
und nachträgliche Änderungen geregelt sein. Eine Funktion für Zertifikate
macht die gesamte Umgebung noch nicht revisionssicher.

## Schnittstellen richtig einordnen

SCORM beschreibt unter anderem den Austausch von Lernpaketen und deren
Kommunikation mit einer Laufzeitumgebung. LTI bindet externe Lernwerkzeuge
an. xAPI beschreibt Lernaktivitätsdaten. H5P liefert interaktive Inhalte;
ein H5P-Paket übernimmt nicht die Benutzerverwaltung eines LMS.
Die konkrete Unterstützung ist pro Plattform und Version zu prüfen.

Bei Moodle ist insbesondere SCORM 1.2 dokumentiert. SCORM 2004 wird vom
Standardmodul nicht vollständig unterstützt; eine pauschale Zusage für beide
Versionen wäre falsch. [Moodle: SCORM FAQ](https://docs.moodle.org/en/SCORM_FAQ).

## Datenhaltung und Auswahl

Die folgende Auswahl betrachtet Moodle und Canvas mit PostgreSQL. Zur
Anwendungsdatenbank kommen Dateien und gegebenenfalls weitere Betriebsdienste.
Die [Bewertungsmethode](software.md) grenzt den betrachteten Speicherumfang ab.
Open edX gehört wegen seines offiziell unterstützten MySQL-Backends nicht
in diese PostgreSQL-Auswahl. [Open edX: Datenbankvorgabe](https://docs.openedx.org/projects/openedx-proposals/en/latest/best-practices/oep-0067-bp-tools-and-technology.html).

## Unterkategorien: gefilterte Softwareauswahl

Die Unterkapitel unterscheiden Einsatzfragen und Bausteine. Heutige Produkte
werden damit nicht zu historischen Vertretern früher Lernsysteme erklärt.

- [Frühe Lernsysteme und heutige Kursräume](lms/cbt-web-lms.md)
- [SCORM und Interoperabilität](lms/scorm-standards.md)
- [Open-Source-LMS](lms/open-source.md)
- [Pflichtschulungen und Nachweise](lms/compliance-enterprise.md)
- [Mobiles und gemischtes Lernen](lms/mobile-blended.md)
- [Cloud-Betrieb und LXP-Anbindung](lms/cloud-lxp.md)

## Open-Source-Auswahl nach Reifegrad

**2 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: 27. September 2026. Auswahl nach der
[gemeinsamen Bewertungsmethode](software.md). Die Reihenfolge priorisiert
Reife und anschließend die Eignung für diese Kategorie.

| Rang | Software | Lizenz des Kerns | Reifegrad | Schwerpunkt | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Moodle](https://github.com/moodle/moodle) | GPL-3.0-or-later | Sehr hoch | Hochschul- und Schul-Lernplattformen | PostgreSQL: [Offizieller pgsql-Treiber](https://docs.moodle.org/all/de/PostgreSQL) |
| 2 | [Canvas LMS](https://github.com/instructure/canvas-lms) | AGPL-3.0 | Sehr hoch | Moderne akademische Lernplattformen | PostgreSQL: [Ausschließlich PostgreSQL](https://github.com/instructure/canvas-lms/wiki/Production-Start) |

## Einsatz und Grenzen

Moodle bietet Kursaktivitäten und Erweiterungsmöglichkeiten. Für die hier
beschriebene Variante wird PostgreSQL als Datenbank gewählt; Plugins müssen
zur eingesetzten Version passen. Moodle Workplace ist gesondert zu betrachten
und wird nicht mit dem frei verfügbaren Moodle-Kern gleichgesetzt.

Canvas verbindet Kursräume, Abgaben und Bewertungen. Eigenbetrieb erfordert
Planung für Datenbank, Dateien, Hintergrundverarbeitung und Aktualisierung.
Eine Schnittstelle zu einem kommerziellen Dienst bedeutet nicht, dass dieser
Dienst Bestandteil des offenen Kerns ist.

Ein Lernportal sollte mit einem vollständigen Beispielkurs geprüft werden:
Anmeldung, Materialzugriff, Abgabe, Bewertung, Export und Wiederherstellung.
Solche Installationstests wurden für dieses Buch nicht durchgeführt.
