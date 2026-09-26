# Local-First- und Synchronisations-Engines

[Übergeordnete Kategorie: Mobile und Desktop-Apps in Content- und Wissenssystemen](../mobile-desktop-apps.md)

Datenabgleich, Konfliktlösung und CRDTs für mobile und Desktop-Wissenssysteme.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Yjs](https://github.com/yjs/yjs) | MIT | Sehr hoch | Führendes CRDT-Framework für kollaborative Echtzeit- und Offline-Bearbeitung. | Dateien: [Binäre CRDT-Zustandsvektoren und Dokumentdateien](https://yjs.dev/) |
| 2 | [Automerge](https://github.com/automerge/automerge) | MIT | Hoch | Dokumentenorientierte CRDT-Bibliothek in Rust und TypeScript für Local-First-Apps. | Dateien: [Kompakte binäre Dokumentdateien](https://automerge.org/) |
| 3 | [RxDB](https://github.com/pubkey/rxdb) | Apache-2.0 | Hoch | Reaktive NoSQL-Client-Datenbank mit Replikationsunterstützung für relationale Backends. | PostgreSQL: [GraphQL- und PostgreSQL-Replikations-Plugin](https://rxdb.info/replication.html) |
| 4 | [WatermelonDB](https://github.com/Nozbe/WatermelonDB) | MIT | Hoch | Hochperformante relationale SQLite-Datenbank für React Native mit Server-Sync. | PostgreSQL: [Synchronisationsprotokoll für relationale Backends](https://watermelondb.dev/) |
| 5 | [PouchDB](https://github.com/pouchdb/pouchdb) | Apache-2.0 | Sehr hoch | Etablierte Offline-First-Datenbank mit bidirektionalem Synchronisationsprotokoll. | Dateien: [Lokaler IndexedDB- und Dateispeicher](https://pouchdb.com/) |

## Einsatz und Abgrenzung

Synchronisations-Engines verhindern Datenverlust bei gleichzeitigen Bearbeitungen ohne aktive Netzwerkverbindung.

- **Yjs:** Extrem performant bei Rich-Text und Block-Editoren; setzt Verbindungs-Server (WebSockets) für Signalisierung voraus.
- **Automerge:** Bildet vollständige JSON-Datenstrukturen als CRDT ab; binäre Updates benötigen Speicherplatzverwaltung.
- **RxDB:** Bietet reaktive Abfragen im Frontend; erfordert strukturierte Replikationsendpunkte auf dem Server.
- **WatermelonDB:** Optimiert auf große Datenmengen in mobilen Apps; setzt React Native oder Web voraus.
- **PouchDB:** Einfache Einrichtung im Browser; Replikationsprotokoll erfordert CouchDB- oder REST-Endpunkte.
