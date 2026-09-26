# Evolution digitaler Docs-as-Code

Docs-as-Code behandelt Dokumentation mit Verfahren aus der Softwareentwicklung:
Textdateien werden versioniert, Änderungen geprüft und Veröffentlichungen
aus den Quellen gebaut.

Die Ausgangsseite unterscheidet sechs Entwicklungsrichtungen:

1. Strukturierte Textauszeichnung und Dokumentation im Quellcode.
2. Zusammenhängende Abläufe aus Versionierung, Review und automatisiertem Build.
3. Markdown als leicht zugängliches Format für Dokumentationsprojekte.
4. Komponenten und interaktive Elemente innerhalb der Dokumentation.
5. KI-Unterstützung für Qualitätsprüfung und dokumentengestützte Suche.
6. Agentische Pflege von Dokumentationsdateien und Änderungen.

Die Übergänge sind fließend. Ein dateibasiertes Buch benötigt weder interaktive
Komponenten noch KI, um einen nachvollziehbaren Pflegeprozess zu ermöglichen.

## Aufbau dieses Buches

Die Inhalte liegen als Markdown vor. `SUMMARY.md` definiert die Lesereihenfolge,
`book.toml` die Buchkonfiguration. mdBook erzeugt daraus die HTML-Ausgabe.

## Unterkategorien: gefilterte Softwareauswahl

- [Strukturierte Textauszeichnung und API-Dokumentation](docs-as-code/strukturierte-texte.md)
- [Versionierung, Review und automatisierter Build](docs-as-code/automatisierte-ablaeufe.md)
- [Markdown-basierte Dokumentation](docs-as-code/markdown.md)
- [Komponenten und interaktive Dokumentation](docs-as-code/komponenten.md)
- [KI-Unterstützung und dokumentengestützte Suche](docs-as-code/ki-unterstuetzung.md)
- [Agentische Dokumentationspflege](docs-as-code/agentische-pflege.md)

## Geplante Vertiefung

- Kapitelstruktur und Querverweise
- Versionierung und redaktionelle Prüfung
- Reproduzierbare Veröffentlichung

Quelle: [Evolution und Architekturen digitaler Docs-as-Code](https://dokument.wissen-ahrensburg.de/wissen/dokumentation/evolution-digitaler-docs-as-code/).

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: 26. September 2026. Redaktionelle Auswahl nach der
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
