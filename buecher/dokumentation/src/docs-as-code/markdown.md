# Markdown-basierte Dokumentation

[Übergeordnete Kategorie: Evolution digitaler Docs-as-Code](../docs-as-code.md)

Textbasierte Bücher und Portale mit überschaubarer Autorenoberfläche.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [MkDocs](https://github.com/mkdocs/mkdocs) | BSD-2-Clause | Sehr hoch | Etablierter Markdown-Generator mit zentraler Konfiguration. | Dateien: [Markdown-Dateien und YAML-Konfiguration](https://github.com/mkdocs/mkdocs) |
| 2 | [Jekyll](https://github.com/jekyll/jekyll) | MIT | Sehr hoch | Langjähriger Generator mit dokumentiertem Ruby-Ökosystem. | Dateien: [Markdown-/HTML-Dateien und Templates](https://github.com/jekyll/jekyll) |
| 3 | [Hugo](https://github.com/gohugoio/hugo) | Apache-2.0 | Sehr hoch | Umfangreiche Dokumentation, Templates und Taxonomien. | Dateien: [Inhaltsdateien und Templates](https://github.com/gohugoio/hugo) |
| 4 | [mdBook](https://github.com/rust-lang/mdBook) | MPL-2.0 | Hoch | Fokussierter Generator mit Benutzerhandbuch. | Dateien: [Markdown- und HTML-Dateien](https://github.com/rust-lang/mdBook) |
| 5 | [Docusaurus](https://github.com/facebook/docusaurus) | MIT | Hoch | Dokumentiertes Framework und Sicherheitsrichtlinie. | Dateien: [Markdown-/MDX-Dateien](https://github.com/facebook/docusaurus) |

## Einsatz und Abgrenzung

Die Konfiguration unterscheidet sich: YAML ist verbreitet, aber keine Voraussetzung. mdBook verwendet TOML und SUMMARY.md.

- **MkDocs:** Theme- und Plugin-Reife separat bewerten.
- **Jekyll:** Ruby-Abhängigkeiten und Plugins müssen zusammenpassen.
- **Hugo:** Redaktionsoberfläche muss separat ergänzt werden.
- **mdBook:** Mehrere Produktversionen und komplexe Portale benötigen zusätzliche Organisation.
- **Docusaurus:** Node.js- und React-Abhängigkeiten gehören zur laufenden Pflege.
