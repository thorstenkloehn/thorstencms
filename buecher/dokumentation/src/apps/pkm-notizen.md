# Local-First PKM- und Wissens-Apps

[Übergeordnete Kategorie: Mobile und Desktop-Apps in Content- und Wissenssystemen](../mobile-desktop-apps.md)

Persönliches Wissensmanagement, Notizen und vernetzte Wissensgraphen auf Desktop und Mobile.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Joplin](https://github.com/laurent22/joplin) | AGPL-3.0 | Sehr hoch | Langjährig etablierte Notiz-App für Desktop und Mobile mit E2EE. | Dateien: [Markdown-Dateien und SQLite-Cache](https://joplinapp.org/) |
| 2 | [SiYuan](https://github.com/siyuan-note/siyuan) | AGPL-3.0 | Sehr hoch | Block-basierter Wissensgraph für Desktop und Mobile mit nativer Synchronisation. | Dateien: [Lokales JSON-Dateisystem im Workspace](https://github.com/siyuan-note/siyuan/blob/master/docs/WORKSPACE.md) |
| 3 | [Logseq](https://github.com/logseq/logseq) | AGPL-3.0 | Hoch | Etablierte Outliner-App für vernetztes Denken auf Desktop und Mobilgeräten. | Dateien: [Lokale Markdown- und Org-Dateien](https://github.com/logseq/logseq) |
| 4 | [Zettlr](https://github.com/Zettlr/Zettlr) | GPL-3.0-or-later | Hoch | Wissenschaftlicher Markdown-Editor für Desktop mit Zettelkasten-Verlinkung. | Dateien: [Lokale Markdown-Quellen und BibTeX-Dateien](https://github.com/Zettlr/Zettlr) |
| 5 | [Foam](https://github.com/foambubble/foam) | MIT | Hoch | Dateibasierte Wissensgraph-Erweiterung für Entwickler-Desktopumgebungen. | Dateien: [Markdown-Dateien im Git-Repository](https://foambubble.github.io/foam/) |

## Einsatz und Abgrenzung

Local-First-Apps gewähren volle Datenkontrolle durch lokale Speicherung direkt auf dem Endgerät.

- **Joplin:** Hervorragend für tägliche Notizen; hierarchische Ordner statt tiefer Wissensgraphen.
- **SiYuan:** Stark bei verknüpften Blöcken; setzt auf ein spezifisches JSON-Dateiformat.
- **Logseq:** Exzellent für tägliche Journale; Datenbank-Version befindet sich noch im Umbau.
- **Zettlr:** Ideal für akademische Texte und Zitate; fokussiert auf Desktop ohne offizielle Mobile-App.
- **Foam:** Nutzt VS Code als Desktop-Umgebung; erfordert Entwickler-Grundkenntnisse.
