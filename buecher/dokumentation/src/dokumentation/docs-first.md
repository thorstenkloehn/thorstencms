# Docs-First: Dokumentationsportale

[Übergeordnete Kategorie: Dokumentenerstellung, Wikis und Notebooks](../dokumentation.md)

Systeme für thematisch gegliederte Dokumentationswebsites.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
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

- **Sphinx:** Etablierter Standard für modulare Softwareportale mit mehrstufiger Seitenhierarchie und Quellcode-Verlinkung.
- **MkDocs:** Ermöglicht die rasche Bereitstellung performanter Dokumentationsportale mit vorkonfigurierter Volltextsuche und responsiver Navigationsleiste.
- **Docusaurus:** Ausgelegt auf umfangreiche Entwicklerportale mit Versionsverwaltung älterer Dokumentationsstände und integrierter Blog-Komponente.
- **VitePress:** Liefert ein reaktionsschnelles Portal-Layout für quelloffene Werkzeuge mit schneller statischer Vorab-Kompilierung.
- **Starlight:** Schlankes Dokumentationsportal auf Astro-Basis mit Fokus auf barrierefreie Seitennavigation und minimalen JavaScript-Ballast im Browser.
