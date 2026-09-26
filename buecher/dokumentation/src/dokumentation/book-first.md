# Book-First: Bücher und Handbücher

[Übergeordnete Kategorie: Dokumentenerstellung, Wikis und Notebooks](../dokumentation.md)

Werkzeuge für zusammenhängende Publikationen mit Kapiteln und festem Lesepfad.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Sphinx](https://github.com/sphinx-doc/sphinx) | BSD-2-Clause | Sehr hoch | Umfangreiches Handbuch und ausgebautes Erweiterungssystem. | Dateien: [reStructuredText-/Markdown-Quellen und HTML-Dateien](https://github.com/sphinx-doc/sphinx) |
| 2 | [Asciidoctor](https://github.com/asciidoctor/asciidoctor) | MIT | Sehr hoch | Dokumentierte Verarbeitungskette mit Tests. | Dateien: [AsciiDoc-Quellen und Ausgabedateien](https://github.com/asciidoctor/asciidoctor) |
| 3 | [Pandoc](https://github.com/jgm/pandoc) | GPL-2.0-or-later | Sehr hoch | Breite Formatunterstützung und dokumentierte Entwicklung. | Dateien: [Markup- und Dokumentdateien](https://github.com/jgm/pandoc) |
| 4 | [mdBook](https://github.com/rust-lang/mdBook) | MPL-2.0 | Hoch | Fokussierter Generator mit Benutzerhandbuch. | Dateien: [Markdown- und HTML-Dateien](https://github.com/rust-lang/mdBook) |
| 5 | [Quarto](https://github.com/quarto-dev/quarto-cli) | MIT | Hoch | Dokumentiertes Projektmodell für Bücher und ausführbare Inhalte. | Dateien: [Markdown-/Notebook-Quellen und Ausgabedateien](https://github.com/quarto-dev/quarto-cli) |

## Einsatz und Abgrenzung

Sphinx und Asciidoctor eignen sich für umfangreiche technische Texte; mdBook ist auf Markdown-Bücher zugeschnitten. Pandoc ist eine Konvertierungsbasis, Quarto ergänzt ausführbare Inhalte.

- **Sphinx:** Erweiterungen müssen im Build aufeinander abgestimmt sein.
- **Asciidoctor:** Für ein vollständiges Portal werden zusätzliche Struktur- und Build-Bausteine benötigt.
- **Pandoc:** Konverter; keine gemeinsame Redaktionsoberfläche.
- **mdBook:** Mehrere Produktversionen und komplexe Portale benötigen zusätzliche Organisation.
- **Quarto:** Codeausführung benötigt passende Laufzeitumgebungen.
