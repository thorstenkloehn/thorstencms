# Visuelle, Local-First und agentische Systeme

[Übergeordnete Kategorie: Digitale Wissenssysteme](../wissenssysteme.md)

Werkzeuge für lokale Wissensarbeit, visuelle Darstellung oder Agentenunterstützung.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
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

- **TiddlyWiki:** Arbeitet vollständig autark im Browser ohne Backend-Server; das Zurückschreiben modifizierter HTML-Dateien verlangt passende Browser-Helfer oder lokale Speicheradapter.
- **Excalidraw:** Ersetzt keine vollständige textuelle Wissensdatenbank.

- **AnythingLLM:** Stellt eine eigenständige Desktop-Laufzeit für lokale Dokumentenabfragen bereit. Die standardmäßige SQLite-Nutzung erfüllt den Buchfilter nicht; zwingend erforderlich ist die [Umstellung auf PostgreSQL und pgvector](../software.md#sonderfall-anythingllm).

- **Zim:** Arbeitet unmittelbar auf dem lokalen Dateisystem; jede Notizseite liegt als gewöhnliche Textdatei im Verzeichnisbaum und bleibt ohne Serversoftware editierbar.

- **SiYuan:** Die .sy-Dateien enthalten das maßgebliche Wissen; die SQLite-Indizes sind rekonstruierbare Hilfsdaten.
