# Dokumentenerstellung, Wikis und interaktive Dokumente

Ein Handbuch für neue Mitarbeitende braucht eine andere Leseführung als die
Referenz einer Programmierschnittstelle. Vor der Werkzeugwahl hilft deshalb
eine konkrete Frage: Was soll jemand mit dem fertigen Inhalt tun können?

## Vom Anwendungsfall zur Dokumentationsform

Für eine Einarbeitung bietet sich eine feste Kapitelreihenfolge an. Zum
Nachschlagen sind kurze, direkt verlinkbare Themenseiten sinnvoll. Wenn das
Ergebnis von Berechnungen überprüfbar bleiben soll, können Notebooks Text,
Code und Ausgabe zusammenhalten. In einem Wiki können mehrere Menschen
Begriffe, Erfahrungen und Entscheidungen über Seitenverweise verbinden.

Diese Formen lassen sich kombinieren. Ein Projekt kann ein Einstiegshandbuch,
eine API-Referenz und eine Sammlung von Betriebsnotizen pflegen. Entscheidend
ist, wo Änderungen vorgenommen werden und wer ihre fachliche Prüfung übernimmt.
Ein zusätzliches Such- oder RAG-System erschließt den Bestand, ersetzt seine
Pflege aber nicht. Automatisch erzeugte Antworten können fehlerhaft sein.

## Beispiel: Betriebsanleitung für einen Dienst

Eine neue Konfigurationsoption erhält eine Referenzseite mit zulässigen Werten.
Das Einstiegskapitel zeigt einen typischen Einsatz. Ein Notebook kann eine
Messung dokumentieren. Alle drei verweisen auf denselben Versionsstand.
So entsteht ein zusammenhängender Bestand, ohne denselben Erklärungstext in
mehreren Kapiteln unabhängig pflegen zu müssen.

## Unterkategorien: gefilterte Softwareauswahl

- [Bücher und Handbücher](dokumentation/book-first.md)
- [Dokumentationsportale](dokumentation/docs-first.md)
- [Notebooks](dokumentation/notebooks.md)
- [Webseiten-Generatoren](dokumentation/webseiten-generatoren.md)
- [Wikis](dokumentation/wikis.md)
- [RAG und Wissenssuche](dokumentation/rag.md)
- [Programmatische Dokumentenerstellung](dokumentation/dokumentenerstellung.md)

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: 27. September 2026. Auswahl nach der
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
