# Markdown-basierte Dokumentation

[Übergeordnete Kategorie: Docs-as-Code](../docs-as-code.md)

Textbasierte Bücher und Portale mit überschaubarer Autorenoberfläche.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
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

- **MkDocs:** Setzt auf Python-Markdown mit solider CommonMark-Konformität; Navigationsbäume werden deklarativ über eine zentrale Konfigurationsdatei gesteuert.
- **Jekyll:** Etablierter Markdown-Standard im Git-Umfeld via Kramdown-Parser und Liquid-Templating; native Ausführung auf GitHub Pages.
- **Hugo:** Bietet durch den integrierten Goldmark-Compiler herausragende Generierungsgeschwindigkeit für sehr große Markdown-Bestände.
- **mdBook:** Konzentriert sich auf reines Markdown ohne komplexe Frontend-Toolchains; die Leseführung wird strikt über die Inhaltsdatei `SUMMARY.md` definiert.
- **Docusaurus:** Erweitert Markdown-Dateien zu MDX, wodurch React-Komponenten direkt im Textfluss eingebunden werden können.
