# Local-First-Architekturen, Offline-RAG und CRDT-Sync

[Übergeordnete Kategorie: Mobile und Desktop-Apps und KI-Framework-SDKs](../apps-ki-integration.md)

Das Local-First-Paradigma postuliert, dass die maßgeblichen Daten einer Anwendung primär auf dem Endgerät des Benutzers liegen. Der Server dient nicht als exklusiver Datenwirt, sondern als Synchronisations- und Backup-Relais. Für KI-Funktionen bedeutet dies: Dokumentenablage, Vektorisierung und semantischer Abruf (RAG) müssen vollständig offline auf dem Smartphone oder Laptop funktionieren.

---

## Eingebettete Vektorspeicher auf dem Client

Auf Mobilgeräten kann kein separater Datenbank-Server betrieben werden. Vektorindizes müssen direkt in den Prozessraum der Applikation eingebettet werden:

```
┌─────────────────────────────────────────────────────────────┐
│ Mobile Applikation (Offline-Zustand)                        │
│                                                             │
│  ┌───────────────────────┐         ┌─────────────────────┐  │
│  │ Lokale Notiz-Dateien  │         │ Kompaktes Embedding-│  │
│  │ (Markdown / JSON)     ├────────►│ Modell (30–80 MB)   │  │
│  └───────────┬───────────┘         └──────────┬──────────┘  │
│              │                                │ Vektoren    │
│              ▼                                ▼             │
│  ┌───────────────────────────────────────────────────────┐  │
│  │ Lokale SQLite-Datenbank mit `sqlite-vec`-Erweiterung  │  │
│  │  ├─ Volltextsuche (FTS5)                              │  │
│  │  └─ Lokale Vektordistanzberechnung (Kosinus / L2)     │  │
│  └───────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

### Technische Komponenten für Offline-RAG:
1. **Lokale Einbettungs-Pipelines:** Kompakte Embedding-Modelle (z. B. MiniLM- oder BGE-Micro-Modelle mit 30 bis 80 Megabyte Binärgröße) berechnen Vektoren in wenigen Millisekunden auf der NPU oder CPU des Telefons.
2. **`sqlite-vec`:** Eine schlanke, in purem C geschriebene Erweiterung für SQLite. Sie erlaubt Vektor-Abfragen (`vec_distance_cosine()`) direkt über vertraute SQL-Statements, ohne dass komplexe externe Vektor-Server installiert werden müssen.
3. **Hybrides lokales Retrieval:** Kombination der bewährten SQLite-Volltextsuche (`FTS5` für lexikalische Exaktheit) mit `sqlite-vec` für semantische Treffer.

---

## Konfliktfreie Synchronisation über CRDTs

Ändert eine Person Notizen offline auf dem Smartphone und parallel im Büro am Webclient, entstehen Versionsdivergenzen. Klassische „Last Write Wins“-Strategien vernichten dabei unwiderruflich Daten.

### Das CRDT-Sync-Modell (Conflict-free Replicated Data Types):
* **Mathematische Konfliktfreiheit:** Bibliotheken wie Automerge oder Yjs zerlegen Textänderungen in kausale Änderungsbäume. Gleichzeitige Bearbeitungen werden deterministisch ohne Datenverlust zusammengeführt.
* **Effiziente Vektor-Synchronisation:** Vektoreinbettungen sind bandbreitenintensiv (ein einziger Vektor belegt mehrere Kilobyte). In modernen Local-First-Architekturen werden über das Mobilfunknetz **nur die Textänderungen (CRDT-Deltas) synchronisiert**.
* **Lokale Nachvektorisierung:** Sobald das Endgerät ein neues Text-Delta empfangen hat, generiert die lokale NPU die neuen Vektoren selbstständig. Dadurch bleibt der mobile Datenverbrauch minimal.

---

## Konsistenzprüfung mit dem PostgreSQL-Zentralserver

Sobald das Endgerät wieder eine stabile Internetverbindung aufbaut, erfolgt der Abgleich mit der zentralen PostgreSQL-Instanz:
1. Das Endgerät sendet seine noch nicht synchronisierten CRDT-Pakete über HTTPS oder WebSockets an das Backend.
2. Das Backend speichert die Änderungen transaktional in PostgreSQL und aktualisiert dort den serverseitigen `pgvector`-Index.
3. Gleichzeitig lädt das Endgerät neu hinzugekommene Dokumente anderer Geräte herunter und aktualisiert seinen lokalen `sqlite-vec`-Bestand.

---

> [!NOTE]
> Wann eine Aufgabe auf dem Endgerät gelöst werden sollte und wann eine Weiterleitung an die Cloud sinnvoll ist, vertieft der Abschnitt [Hybrid-Routing, Modellkaskadierung und Energiemanagement](hybrid-routing-energiemanagement.md).
