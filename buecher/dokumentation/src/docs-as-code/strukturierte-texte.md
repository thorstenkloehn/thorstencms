# Strukturierte Textauszeichnung und API-Dokumentation

[Übergeordnete Kategorie: Docs-as-Code](../docs-as-code.md)

Werkzeuge für strukturierten Text, Quellcode-Referenzen und reproduzierbare Ausgabe.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Doxygen](https://www.doxygen.nl/manual/index.html) | GPL-2.0 | Sehr hoch | Langjährig eingesetzt; umfassendes Referenzhandbuch. | Dateien: [Quellcode-/Textdateien und generierte Referenzen](https://www.doxygen.nl/manual/index.html) |
| 2 | [Sphinx](https://github.com/sphinx-doc/sphinx) | BSD-2-Clause | Sehr hoch | Umfangreiches Handbuch und ausgebautes Erweiterungssystem. | Dateien: [reStructuredText-/Markdown-Quellen und HTML-Dateien](https://github.com/sphinx-doc/sphinx) |
| 3 | [Asciidoctor](https://github.com/asciidoctor/asciidoctor) | MIT | Sehr hoch | Dokumentierte Verarbeitungskette mit Tests. | Dateien: [AsciiDoc-Quellen und Ausgabedateien](https://github.com/asciidoctor/asciidoctor) |
| 4 | [Pandoc](https://github.com/jgm/pandoc) | GPL-2.0-or-later | Sehr hoch | Breite Formatunterstützung und dokumentierte Entwicklung. | Dateien: [Markup- und Dokumentdateien](https://github.com/jgm/pandoc) |
| 5 | [Jekyll](https://github.com/jekyll/jekyll) | MIT | Sehr hoch | Langjähriger Generator mit dokumentiertem Ruby-Ökosystem. | Dateien: [Markdown-/HTML-Dateien und Templates](https://github.com/jekyll/jekyll) |

## Einsatz und Abgrenzung

Die Liste nennt heutige Werkzeuge für das Architekturprinzip. Sie ist keine Behauptung, alle Projekte seien bereits in der historischen Vorläufergeneration entstanden.

- **Doxygen:** Etablierter Standard zur Extraktion strukturierter Schnittstellenreferenzen direkt aus Quellcode-Kommentaren (C++, Java, C).
- **Sphinx:** Führend bei semantischen Querverweisen in reStructuredText und MyST-Markdown mit präziser Typprüfung für Programmiersprachen-Domänen.
- **Asciidoctor:** Leistungsfähige AsciiDoc-Verarbeitung für technische Dokumente mit modularen Dateieinbindungen (`include`), Callouts und bedingter Kompilierung.
- **Pandoc:** Dient als universelle Syntax-Brücke zur formatverlustarmen Transformation zwischen unterschiedlichen Auszeichnungssprachen.
- **Jekyll:** Kombiniert Markdown-Texte mit strukturierten YAML-Frontmatter-Metadaten für templategestützte Publikationsprozesse.
