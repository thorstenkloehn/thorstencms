# Webseiten-Generatoren

[Übergeordnete Kategorie: Dokumentenerstellung, Wikis und Notebooks](../dokumentation.md)

Statische Veröffentlichung allgemeiner Informationsseiten und Blogs.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Hugo](https://github.com/gohugoio/hugo) | Apache-2.0 | Sehr hoch | Umfangreiche Dokumentation, Templates und Taxonomien. | Dateien: [Inhaltsdateien und Templates](https://github.com/gohugoio/hugo) |
| 2 | [Jekyll](https://github.com/jekyll/jekyll) | MIT | Sehr hoch | Langjähriger Generator mit dokumentiertem Ruby-Ökosystem. | Dateien: [Markdown-/HTML-Dateien und Templates](https://github.com/jekyll/jekyll) |
| 3 | [Pelican](https://github.com/getpelican/pelican) | AGPL-3.0 | Hoch | Dokumentierter Python-Generator für Markdown und reStructuredText. | Dateien: [Markdown-/reStructuredText-Dateien](https://github.com/getpelican/pelican) |
| 4 | [Build Awesome (Eleventy)](https://github.com/11ty/buildawesome) | MIT | Hoch | Dokumentierter Template-Generator mit Eleventy-Kompatibilität. | Dateien: [Inhalts- und Template-Dateien](https://github.com/11ty/buildawesome) |
| 5 | [Astro](https://github.com/withastro/astro) | MIT | Hoch | Dokumentation, Sicherheitsrichtlinie und offene Governance. | Dateien: [Markdown-/MDX-Dateien und Komponenten](https://github.com/withastro/astro) |

## Einsatz und Abgrenzung

Die Auswahl priorisiert langjährige Generatoren; Astro ergänzt komponentenbasierte Seiten. Build Awesome führt die Eleventy-Linie fort.

- **Hugo:** Eignet sich hervorragend für inhaltsstarke Webauftritte und Blogs mit hierarchischen Taxonomien und schnellem Live-Reload beim Verfassen von Beiträgen.
- **Jekyll:** Klassischer seitenbasierter Blog-Generator mit nativer Datums- und Artikellogik, unterstützt durch das weltweite GitHub-Pages-Hosting.
- **Pelican:** Flexibler Python-Generator mit Jinja2-Templating, ideal für mehrsprachige Content-Websites ohne JavaScript-Buildschritt.
- **Build Awesome (Eleventy):** Extrem flexibler statischer Generator mit freier Vorlagenwahl (Nunjucks, Liquid, Markdown) und schlanker Ausgabestruktur.
- **Astro:** Optimiert für inhaltsgetriebene Marketing- und Informationsseiten; liefert standardmäßig null Kilobyte Client-JavaScript aus.
