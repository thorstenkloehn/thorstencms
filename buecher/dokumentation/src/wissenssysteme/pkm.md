# Persönliche Wissensgraphen und Block-Editoren

[Übergeordnete Kategorie: Evolution digitaler Wissenssysteme](../wissenssysteme.md)

Vernetzte Notizen, Wissenseinheiten und persönliche Wissensorganisation.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [TiddlyWiki](https://github.com/TiddlyWiki/TiddlyWiki5) | BSD-3-Clause | Hoch | Langjähriges Projekt mit portabler Architektur. | Dateien: [Einzelne HTML-Datei mit eingebetteten Inhalten](https://tiddlywiki.com/dev/static/Data%2520Storage%2520in%2520Single%2520File%2520TiddlyWiki.html) |
| 2 | [Org-roam](https://github.com/org-roam/org-roam) | GPL-3.0-or-later | Hoch | Dokumentierte Rückverweise und Integration in Org-mode. | Dateien: [Org-Textdateien; SQLite nur als Cache](https://www.orgroam.com/manual) |
| 3 | [SiYuan](https://github.com/siyuan-note/siyuan) | AGPL-3.0 | Hoch | Dokumentiertes lokales Wissenssystem mit offenem Kern. | Dateien: [JSON-Inhaltsdateien (.sy); Index rekonstruierbar](https://github.com/siyuan-note/siyuan/blob/master/docs/WORKSPACE.md) |
| 4 | [Zettlr](https://github.com/Zettlr/Zettlr) | GPL-3.0 | Hoch | Dokumentierter Zettelkasten-Workflow mit Graphansicht und Änderungsverlauf. | Dateien: [Markdown-Dateien](https://github.com/Zettlr/Zettlr) |
| 5 | [Zim](https://github.com/zim-desktop-wiki/zim-desktop-wiki) | GPL-2.0-or-later | Hoch | Langjähriges Desktop-Wiki mit verlinkten Notizen und Handbuch. | Dateien: [Wiki-Textdateien und Anhänge](https://zim-wiki.org/) |

## Einsatz und Abgrenzung

Die Auswahl verbindet vernetzte Notizen mit unterschiedlichen Arbeitsoberflächen. SiYuan setzt auf Blöcke, Org-roam auf Emacs; Zettlr verbindet Markdown-Texte mit einer dokumentierten Graphansicht.

- **TiddlyWiki:** Gemeinsame Bearbeitung und Synchronisierung brauchen ein passendes Betriebskonzept.
- **Org-roam:** Erfordert Emacs- und Org-mode-Kenntnisse.
- **SiYuan:** Synchronisierung und Zusatzdienste separat beurteilen.
- **Zettlr:** Schwerpunkt auf persönlicher Text- und Wissensarbeit; keine zentrale Teamredaktion.

Funktionsnachweis: [Zettlr-Graphansicht](https://docs.zettlr.com/en/pkms/graph.html).

- **Zim:** Lokale, verlinkte Wiki-Seiten liegen in Textdateien. Der Schwerpunkt liegt auf persönlicher Wissensarbeit, nicht auf gemeinsamem Echtzeit-Editing.
