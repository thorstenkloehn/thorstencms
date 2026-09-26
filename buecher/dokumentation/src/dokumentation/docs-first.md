# Docs-First: Dokumentationsportale

[Übergeordnete Kategorie: Dokumentenerstellung, Wikis und Notebooks](../dokumentation.md)

Systeme für thematisch gegliederte Dokumentationswebsites.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Sphinx](https://github.com/sphinx-doc/sphinx) | BSD-2-Clause | Sehr hoch | Umfangreiches Handbuch und ausgebautes Erweiterungssystem. | Dateien: [reStructuredText-/Markdown-Quellen und HTML-Dateien](https://github.com/sphinx-doc/sphinx) |
| 2 | [MkDocs](https://github.com/mkdocs/mkdocs) | BSD-2-Clause | Sehr hoch | Etablierter Markdown-Generator mit zentraler Konfiguration. | Dateien: [Markdown-Dateien und YAML-Konfiguration](https://github.com/mkdocs/mkdocs) |
| 3 | [Docusaurus](https://github.com/facebook/docusaurus) | MIT | Hoch | Dokumentiertes Framework und Sicherheitsrichtlinie. | Dateien: [Markdown-/MDX-Dateien](https://github.com/facebook/docusaurus) |
| 4 | [VitePress](https://github.com/vuejs/vitepress) | MIT | Hoch | Dokumentation, Änderungsverlauf und Vue-Integration. | Dateien: [Markdown-Dateien](https://github.com/vuejs/vitepress) |
| 5 | [Starlight](https://github.com/withastro/starlight) | MIT | Hoch | Eigene Dokumentation und Einbindung ins Astro-Projekt. | Dateien: [Markdown-/MDX-Dateien](https://github.com/withastro/starlight) |

## Einsatz und Abgrenzung

Die beiden etablierten Generatoren stehen vor den stärker komponentenorientierten Frameworks. Interaktivität ist eine zusätzliche Anforderung, kein Reifebeleg.

- **Sphinx:** Erweiterungen müssen im Build aufeinander abgestimmt sein.
- **MkDocs:** Theme- und Plugin-Reife separat bewerten.
- **Docusaurus:** Node.js- und React-Abhängigkeiten gehören zur laufenden Pflege.
- **VitePress:** Komponenten benötigen Vue-Kenntnisse.
- **Starlight:** Astro-Komponenten und Erweiterungen müssen kompatibel sein.
