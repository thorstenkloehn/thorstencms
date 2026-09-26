# Visuelle, Local-First und agentische Systeme

[Übergeordnete Kategorie: Evolution digitaler Wissenssysteme](../wissenssysteme.md)

Werkzeuge für lokale Wissensarbeit, visuelle Darstellung oder Agentenunterstützung.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [TiddlyWiki](https://github.com/TiddlyWiki/TiddlyWiki5) | BSD-3-Clause | Hoch | Langjähriges Projekt mit portabler Architektur. | Dateien: [Einzelne HTML-Datei mit eingebetteten Inhalten](https://tiddlywiki.com/dev/static/Data%2520Storage%2520in%2520Single%2520File%2520TiddlyWiki.html) |
| 2 | [Excalidraw](https://github.com/excalidraw/excalidraw) | MIT | Hoch | Dokumentierte offene Zeichenanwendung und Komponenten. | Dateien: [Lokale Zeichnungsdateien (.excalidraw/JSON)](https://github.com/excalidraw/excalidraw) |
| 3 | [Zim](https://github.com/zim-desktop-wiki/zim-desktop-wiki) | GPL-2.0-or-later | Hoch | Langjähriges Desktop-Wiki mit verlinkten Notizen und Handbuch. | Dateien: [Wiki-Textdateien und Anhänge](https://zim-wiki.org/) |
| 4 | [SiYuan](https://github.com/siyuan-note/siyuan) | AGPL-3.0 | Hoch | Dokumentiertes lokales Wissenssystem mit offenem Kern. | Dateien: [JSON-Inhaltsdateien (.sy); Index rekonstruierbar](https://github.com/siyuan-note/siyuan/blob/master/docs/WORKSPACE.md) |
| 5 | [AnythingLLM](https://github.com/Mintplex-Labs/anything-llm) | MIT (Kern) | Mittel für PostgreSQL-Betrieb | PostgreSQL-Pfad im Quellprojekt beschrieben; zusätzliche Einrichtung erforderlich. | PostgreSQL: [Prisma-Datenbank umstellen](https://github.com/Mintplex-Labs/anything-llm/blob/master/server/prisma/schema.prisma) und [pgvector konfigurieren](https://github.com/Mintplex-Labs/anything-llm/blob/master/server/utils/vectorDbProviders/pgvector/SETUP.md) |

## Einsatz und Abgrenzung

Die gefilterte Auswahl deckt lokale Wissensarbeit und visuelle Darstellung ab: TiddlyWiki speichert eine HTML-Datei, Excalidraw lokale Zeichnungsdateien. AnythingLLM ergänzt Agentenfunktionen, hier ausschließlich in der angepassten PostgreSQL-Variante.

- **TiddlyWiki:** Gemeinsame Bearbeitung und Synchronisierung brauchen ein passendes Betriebskonzept.
- **Excalidraw:** Ersetzt keine vollständige textuelle Wissensdatenbank.


- **AnythingLLM:** Nur der PostgreSQL-Betrieb bleibt ausgewählt: Prisma-Datenbank gemäß Quellhinweis umstellen und pgvector als Vektorspeicher einrichten. Die Standardinstallation mit SQLite erfüllt den Filter nicht. Dieser zusätzliche Anpassungsbedarf begrenzt die Reife dieser Betriebsvariante.

- **Zim:** Lokale, verlinkte Wiki-Seiten liegen in Textdateien. Der Schwerpunkt liegt auf persönlicher Wissensarbeit, nicht auf gemeinsamem Echtzeit-Editing.

- **SiYuan:** Die .sy-Dateien enthalten das maßgebliche Wissen; die SQLite-Indizes sind rekonstruierbare Hilfsdaten.
