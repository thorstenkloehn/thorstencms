# Docs-as-Code: Änderungen gemeinsam prüfen

Bei Docs-as-Code liegen Dokumente in bearbeitbaren Textdateien. Änderungen
werden versioniert, geprüft und anschließend in ein lesbares Ausgabeformat
überführt. Der Nutzen zeigt sich besonders dann, wenn Dokumentation und
Software häufig gemeinsam geändert werden.

## Beispiel: Eine geänderte Konfigurationsoption

Ein Änderungsvorschlag enthält den neuen Programmcode, die überarbeitete
Erklärung und ein passendes Beispiel. Die prüfende Person sieht zusammen,
ob Beschreibung und Verhalten übereinstimmen. Ein Build kontrolliert, ob sich
das Buch erzeugen lässt. Zusätzliche Prüfungen können fehlende Links oder
abweichende Begriffe melden; fachliche Richtigkeit folgt daraus nicht automatisch.

## Wiederholbare Veröffentlichung

Für verlässliche Ergebnisse müssen Werkzeugversionen, Erweiterungen und
benötigte Dateien festgelegt werden. Allein die Verwendung von Git oder
Markdown macht einen Build weder deterministisch noch offlinefähig.
Auch Barrierefreiheit hängt von Inhalt, Struktur, Theme und Ausgabe ab.

KI-Werkzeuge können Änderungen vorbereiten. Ihre Ergebnisse werden als
Textänderungen geprüft, bevor der eigentliche Publikationslauf beginnt.
Dadurch bleibt nachvollziehbar, welcher Text veröffentlicht wurde.

## Aufbau dieses Buches

Die Inhalte liegen als Markdown vor. `SUMMARY.md` ordnet die Kapitel,
`book.toml` konfiguriert mdBook. Für eine Änderung werden Inhalt und
Querverweise geprüft, danach wird die HTML-Ausgabe gebaut und kontrolliert.

## Unterkategorien: gefilterte Softwareauswahl

- [Textauszeichnung und API-Dokumentation](docs-as-code/strukturierte-texte.md)
- [Versionierung, Review und Build](docs-as-code/automatisierte-ablaeufe.md)
- [Markdown-Dokumentation](docs-as-code/markdown.md)
- [Komponenten und Interaktion](docs-as-code/komponenten.md)
- [KI und dokumentengestützte Suche](docs-as-code/ki-unterstuetzung.md)
- [Agentische Dokumentationspflege](docs-as-code/agentische-pflege.md)

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: 27. September 2026. Auswahl nach der
[gemeinsamen Bewertungsmethode](software.md). Die Reihenfolge priorisiert
Reife und anschließend die Eignung für diese Kategorie.

| Rang | Software | Lizenz des Kerns | Reifegrad | Schwerpunkt | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Sphinx](https://github.com/sphinx-doc/sphinx) | BSD-2-Clause | Sehr hoch | Umfangreiche technische Dokumentation | Dateien: [reStructuredText-/Markdown-Quellen und HTML-Dateien](https://github.com/sphinx-doc/sphinx) |
| 2 | [Doxygen](https://www.doxygen.nl/manual/index.html) | GPL-2.0 | Sehr hoch | Automatisierte API-Referenzen | Dateien: [Quellcode-/Textdateien und generierte Referenzen](https://www.doxygen.nl/manual/index.html) |
| 3 | [Asciidoctor](https://github.com/asciidoctor/asciidoctor) | MIT | Sehr hoch | Strukturierte technische Texte in AsciiDoc | Dateien: [AsciiDoc-Quellen und Ausgabedateien](https://github.com/asciidoctor/asciidoctor) |
| 4 | [Docusaurus](https://github.com/facebook/docusaurus) | MIT | Hoch | Dokumentationsportale mit Komponenten | Dateien: [Markdown-/MDX-Dateien](https://github.com/facebook/docusaurus) |
| 5 | [mdBook](https://github.com/rust-lang/mdBook) | MPL-2.0 | Hoch | Versionierte Markdown-Handbücher | Dateien: [Markdown- und HTML-Dateien](https://github.com/rust-lang/mdBook) |

### 1. Sphinx

**Begründung:** Querverweise, API-Erweiterungen und mehrere Ausgabeformate bilden eine belastbare Publikationsbasis.

**Einordnung:** Erweiterungen müssen im Build aufeinander abgestimmt sein.

Offizielle Grundlage: [Sphinx](https://github.com/sphinx-doc/sphinx).

### 2. Doxygen

**Begründung:** Langjährig eingesetzter Generator mit umfassendem Konfigurations- und Referenzhandbuch.

**Einordnung:** Ein vollständiger Review- und Veröffentlichungsprozess kommt aus der Umgebung.

Offizielle Grundlage: [Doxygen](https://www.doxygen.nl/manual/index.html).

### 3. Asciidoctor

**Begründung:** Seit 2012 entwickelte Verarbeitungskette mit dokumentierter Nutzung, Tests und mehreren Ausgabewegen.

**Einordnung:** Für ein vollständiges Portal werden zusätzliche Struktur- und Build-Bausteine benötigt.

Offizielle Grundlage: [Asciidoctor](https://github.com/asciidoctor/asciidoctor).

### 4. Docusaurus

**Begründung:** Etabliertes Dokumentationsframework mit dokumentierter Entwicklung und Sicherheitsrichtlinie.

**Einordnung:** Node.js- und React-Abhängigkeiten gehören zur laufenden Pflege.

Offizielle Grundlage: [Docusaurus](https://github.com/facebook/docusaurus).

### 5. mdBook

**Begründung:** Dokumentierter, fokussierter Build-Prozess und einfache Navigation über SUMMARY.md.

**Einordnung:** Mehrere Produktversionen und komplexe Portale benötigen zusätzliche Organisation.

Offizielle Grundlage: [mdBook](https://github.com/rust-lang/mdBook).
