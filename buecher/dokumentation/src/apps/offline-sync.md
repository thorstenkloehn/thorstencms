# Local-First- und Synchronisations-Engines

[Übergeordnete Kategorie: Mobile und Desktop-Apps in Content- und Wissenssystemen](../mobile-desktop-apps.md)

Datenabgleich, Konfliktlösung und CRDTs für mobile und Desktop-Wissenssysteme.

## Open-Source-Auswahl nach Reifegrad

**2 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Yjs](https://github.com/yjs/yjs) | MIT | Sehr hoch | CRDT-Bibliothek für eigene kollaborative Anwendungen. | Dateien: [Vollständiger Zustand als binäres Update; Dateiablage selbst implementieren](https://yjs.dev/) |
| 2 | [Automerge](https://github.com/automerge/automerge) | MIT | Hoch | Dokumentenorientierte CRDT-Bibliothek in Rust und TypeScript für Local-First-Apps. | Dateien: [Kompakte binäre Dokumentdateien](https://automerge.org/) |

## Einsatz und Abgrenzung

Yjs und Automerge liefern Datenstrukturen und Änderungsformate für eigene
Anwendungen. Transport, dauerhafte Speicherung, Wiederherstellung und
Zugriffskontrolle sind zusätzliche Aufgaben.

Bei Yjs kann ein vollständiger Zustand als binäres Update serialisiert werden.
Ein Zustandsvektor allein enthält nicht den vollständigen Dokumentinhalt.
Die Anwendung muss das Update in eine Datei schreiben und beim Start wieder
laden. [Yjs: Document Updates](https://docs.yjs.dev/api/document-updates).

Automerge unterstützt ein eigenes Dokumentmodell. Serialisierung und Laden
werden mit der Dateiverwaltung der Anwendung verbunden.
[Automerge: Dokumentmodell](https://automerge.org/docs/reference/documents/).

Yjs ist nicht auf WebSockets festgelegt. Ein Transport wird passend zur
Anwendung gewählt. Beide Bibliotheken können Änderungen zusammenführen,
garantieren aber keine fachlich richtige Bearbeitung oder verlustfreie
Gesamtanwendung. Ein Test sollte gleichzeitige Änderungen, Verbindungsabbrüche
und Wiederherstellung nach einem Neustart einschließen.
