# Dokumentenerstellung, Wikis und Notebooks

Dokumentation kann als fortlaufendes Buch, als vernetzte Sammlung oder als
ausführbares Dokument organisiert sein. Die Ausgangsübersicht unterscheidet
mehrere Aufgabenfelder:

| Form | Schwerpunkt |
| --- | --- |
| Book-First | Zusammenhängende Bücher und Handbücher mit Lesereihenfolge |
| Docs-First | Thematisch gegliederte Dokumentationsportale und Referenzen |
| Notebooks | Text, Berechnungen und Ergebnisse in einem Dokument |
| Webseiten-Generatoren | Veröffentlichung allgemeiner Informationsseiten |
| Wikis und Wissensdatenbanken | Gemeinsam gepflegte, verknüpfte Inhalte |
| RAG- und KI-Wissenssysteme | Suche und Antworten auf Basis eines Dokumentbestands |
| Programmatische Dokumentenerstellung | Wiederholbare Erzeugung von Dokumenten aus Daten |

Diese Formen überschneiden sich. Ein Buch kann Teil eines Wissensportals sein;
ein Wiki kann ergänzend eine dokumentengestützte KI-Suche anbieten.

## Unterkategorien: gefilterte Softwareauswahl

- [Book-First: Bücher und Handbücher](dokumentation/book-first.md)
- [Docs-First: Dokumentationsportale](dokumentation/docs-first.md)
- [Notebooks und ausführbare Dokumente](dokumentation/notebooks.md)
- [Webseiten-Generatoren](dokumentation/webseiten-generatoren.md)
- [Wikis und Wissensdatenbanken](dokumentation/wikis.md)
- [RAG- und KI-Wissenssysteme](dokumentation/rag.md)
- [Programmatische Dokumentenerstellung](dokumentation/dokumentenerstellung.md)

## Geplante Vertiefung

- Zielgruppen und Lesewege
- Dokumentstruktur und Querverweise
- Pflege, Verantwortlichkeiten und Veröffentlichung

Quelle: [Dokumentenerstellung, Wikis & Notebooks](https://dokument.wissen-ahrensburg.de/wissen/dokumentation/).

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: 26. September 2026. Redaktionelle Auswahl nach der
[gemeinsamen Bewertungsmethode](software.md). Die Reihenfolge priorisiert
Reife und anschließend die Eignung für diese Kategorie.

| Rang | Software | Lizenz des Kerns | Reifegrad | Schwerpunkt | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Sphinx](https://github.com/sphinx-doc/sphinx) | BSD-2-Clause | Sehr hoch | Handbücher und technische Referenzen | Dateien: [reStructuredText-/Markdown-Quellen und HTML-Dateien](https://github.com/sphinx-doc/sphinx) |
| 2 | [Pandoc](https://github.com/jgm/pandoc) | GPL-2.0-or-later | Sehr hoch | Dokumentkonvertierung und Veröffentlichung | Dateien: [Markup- und Dokumentdateien](https://github.com/jgm/pandoc) |
| 3 | [Doxygen](https://www.doxygen.nl/manual/index.html) | GPL-2.0 | Sehr hoch | Quellcode- und API-Dokumentation | Dateien: [Quellcode-/Textdateien und generierte Referenzen](https://www.doxygen.nl/manual/index.html) |
| 4 | [JupyterLab](https://github.com/jupyterlab/jupyterlab) | BSD-3-Clause | Sehr hoch | Interaktive Notebooks | Dateien: [Notebook-Dateien (.ipynb)](https://github.com/jupyterlab/jupyterlab) |
| 5 | [mdBook](https://github.com/rust-lang/mdBook) | MPL-2.0 | Hoch | Markdown-Bücher | Dateien: [Markdown- und HTML-Dateien](https://github.com/rust-lang/mdBook) |

### 1. Sphinx

**Begründung:** Umfangreiche Querverweise, mehrere Ausgabeformate und ein etabliertes Erweiterungssystem.

**Einordnung:** Erweiterungen und Ausgabeformate erhöhen den Konfigurationsaufwand.

Offizielle Grundlage: [Sphinx](https://github.com/sphinx-doc/sphinx).

### 2. Pandoc

**Begründung:** Breite Formatunterstützung, ausführliches Handbuch und nachvollziehbare Entwicklung.

**Einordnung:** Konverter; keine gemeinsame Redaktionsoberfläche.

Offizielle Grundlage: [Pandoc](https://github.com/jgm/pandoc).

### 3. Doxygen

**Begründung:** Langjähriger Einsatz in Softwareprojekten; detailliertes Handbuch und dokumentierte Ausgabeformate.

**Einordnung:** Schwerpunkt auf Quellcode; redaktionelle Inhalte brauchen zusätzliche Struktur.

Offizielle Grundlage: [Doxygen](https://www.doxygen.nl/manual/index.html).

### 4. JupyterLab

**Begründung:** Etabliertes Notebook-Ökosystem mit Dokumentation, Erweiterungen und Gemeinschaftsstrukturen.

**Einordnung:** Reproduzierbare Ausführung hängt zusätzlich von Kerneln und Abhängigkeiten ab.

Offizielle Grundlage: [JupyterLab](https://github.com/jupyterlab/jupyterlab).

### 5. mdBook

**Begründung:** Fokussierter Buchgenerator mit eigenem Benutzerhandbuch, Änderungsverlauf und überschaubarer Struktur.

**Einordnung:** Für komplexe Publikationsformate sind zusätzliche Werkzeuge nötig.

Offizielle Grundlage: [mdBook](https://github.com/rust-lang/mdBook).
