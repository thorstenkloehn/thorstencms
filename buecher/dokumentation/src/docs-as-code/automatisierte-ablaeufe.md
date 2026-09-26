# Versionierung, Review und automatisierter Build

[Übergeordnete Kategorie: Docs-as-Code](../docs-as-code.md)

Generatoren als Bausteine eines nachvollziehbaren Dokumentationsprozesses.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Sphinx](https://github.com/sphinx-doc/sphinx) | BSD-2-Clause | Sehr hoch | Umfangreiches Handbuch und ausgebautes Erweiterungssystem. | Dateien: [reStructuredText-/Markdown-Quellen und HTML-Dateien](https://github.com/sphinx-doc/sphinx) |
| 2 | [Doxygen](https://www.doxygen.nl/manual/index.html) | GPL-2.0 | Sehr hoch | Langjährig eingesetzt; umfassendes Referenzhandbuch. | Dateien: [Quellcode-/Textdateien und generierte Referenzen](https://www.doxygen.nl/manual/index.html) |
| 3 | [Asciidoctor](https://github.com/asciidoctor/asciidoctor) | MIT | Sehr hoch | Dokumentierte Verarbeitungskette mit Tests. | Dateien: [AsciiDoc-Quellen und Ausgabedateien](https://github.com/asciidoctor/asciidoctor) |
| 4 | [MkDocs](https://github.com/mkdocs/mkdocs) | BSD-2-Clause | Sehr hoch | Etablierter Markdown-Generator mit zentraler Konfiguration. | Dateien: [Markdown-Dateien und YAML-Konfiguration](https://github.com/mkdocs/mkdocs) |
| 5 | [mdBook](https://github.com/rust-lang/mdBook) | MPL-2.0 | Hoch | Fokussierter Generator mit Benutzerhandbuch. | Dateien: [Markdown- und HTML-Dateien](https://github.com/rust-lang/mdBook) |

## Einsatz und Abgrenzung

Git, Review und CI müssen die Generatoren ergänzen. Bewertet werden hier die Dokumentationswerkzeuge, nicht vollständige Hosting- oder CI-Plattformen.

- **Sphinx:** Lässt sich über `sphinx-build -W` deterministisch in CI-Pipelines einbinden, um unvollständige Verweise sofort als Build-Fehler zu stoppen.
- **Doxygen:** Ermöglicht automatisierte API-Dokumentationsläufe direkt nach Code-Commits; erfordert Abstimmung mit dem Compiler-Build-System.
- **Asciidoctor:** Schnelle, containerfreundliche Pipeline-Ausführung zur gleichzeitigen Erzeugung von HTML5- und PDF-Releases bei neuen Softwareversionen.
- **MkDocs:** Ermöglicht über den Schalter `--strict` automatisierte Prüfungen auf fehlerhafte Links und fehlende Navigationsziele im CI-Lauf.
- **mdBook:** Minimaler Ressourcenbedarf und extrem schneller nativer Build; hervorragend für leichtgewichtige GitHub-Pages- und CI-Workflows ohne Laufzeit-Overhead geeignet.
