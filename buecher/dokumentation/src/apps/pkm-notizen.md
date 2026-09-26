# Local-First PKM- und Wissens-Apps

[Übergeordnete Kategorie: Mobile und Desktop-Apps in Content- und Wissenssystemen](../mobile-desktop-apps.md)

Persönliches Wissensmanagement, Notizen und vernetzte Wissensgraphen auf Desktop und Mobile.

## Open-Source-Auswahl nach Reifegrad

**3 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [SiYuan](https://github.com/siyuan-note/siyuan) | AGPL-3.0 | Hoch | Block-basierter Wissensgraph für Desktop und Mobile mit nativer Synchronisation. | Dateien: [Lokales JSON-Dateisystem im Workspace](https://github.com/siyuan-note/siyuan/blob/master/docs/WORKSPACE.md) |
| 2 | [Zettlr](https://github.com/Zettlr/Zettlr) | GPL-3.0-or-later | Hoch | Wissenschaftlicher Markdown-Editor für Desktop mit Zettelkasten-Verlinkung. | Dateien: [Lokale Markdown-Quellen und BibTeX-Dateien](https://github.com/Zettlr/Zettlr) |
| 3 | [Foam](https://github.com/foambubble/foam) | MIT | Hoch | Dateibasierte Wissensgraph-Erweiterung für Entwickler-Desktopumgebungen. | Dateien: [Markdown-Dateien im Git-Repository](https://foambubble.github.io/foam/) |

## Einsatz und Abgrenzung

SiYuan speichert den betrachteten Inhalt in .sy-Dateien; seine Hilfsindizes
sind davon zu unterscheiden. Zettlr arbeitet an Markdown-Dateien, Foam
verbindet solche Dateien innerhalb einer Editorumgebung.

Für persönliche Notizen zählt neben dem Dateiformat, wie Verweise, Anhänge
und Änderungen auf mehreren Geräten behandelt werden. Eine Anwendung mit
lokaler Speicherung besitzt nicht automatisch eine passende mobile Oberfläche
oder sichere Synchronisation. Diese Funktionen sind vor einem Wechsel separat
zu prüfen.
