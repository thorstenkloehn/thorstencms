# Programmatische Dokumentenerstellung

[Übergeordnete Kategorie: Dokumentenerstellung, Wikis und Notebooks](../dokumentation.md)

Automatisierbare Konvertierung und Erzeugung von Dokumenten.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Pandoc](https://github.com/jgm/pandoc) | GPL-2.0-or-later | Sehr hoch | Breite Formatunterstützung und dokumentierte Entwicklung. | Dateien: [Markup- und Dokumentdateien](https://github.com/jgm/pandoc) |
| 2 | [Asciidoctor](https://github.com/asciidoctor/asciidoctor) | MIT | Sehr hoch | Dokumentierte Verarbeitungskette mit Tests. | Dateien: [AsciiDoc-Quellen und Ausgabedateien](https://github.com/asciidoctor/asciidoctor) |
| 3 | [nbconvert](https://github.com/jupyter/nbconvert) | BSD-3-Clause | Sehr hoch | Dokumentierter Jupyter-Baustein mit Release-Prozess. | Dateien: [Notebook-Dateien und Exporte](https://github.com/jupyter/nbconvert) |
| 4 | [python-docx](https://github.com/python-openxml/python-docx) | MIT | Hoch | Dokumentierte API und Versionshistorie für DOCX-Dateien. | Dateien: [DOCX-Dateien](https://github.com/python-openxml/python-docx) |
| 5 | [PHPWord](https://github.com/PHPOffice/PHPWord) | LGPL-3.0 | Hoch | Dokumentation, kontinuierliche Integration und Unit-Tests. | Dateien: [Dokumentdateien, etwa DOCX und ODT](https://github.com/PHPOffice/PHPWord) |

## Einsatz und Abgrenzung

Die Auswahl umfasst Konverter und Bibliotheken: DOCX-Verarbeitung, strukturierte Texte und Notebook-Exporte erfüllen unterschiedliche Aufgaben.

- **Pandoc:** Konverter; keine gemeinsame Redaktionsoberfläche.
- **Asciidoctor:** Für ein vollständiges Portal werden zusätzliche Struktur- und Build-Bausteine benötigt.
- **nbconvert:** Keine eigenständige Oberfläche zur gemeinsamen Redaktion.
- **python-docx:** Die erzeugten Dateien müssen im Zielprogramm geprüft werden.
- **PHPWord:** Ausgabeformate können unterschiedliche Funktionen abdecken.
