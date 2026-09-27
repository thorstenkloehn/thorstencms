# Asynchrone Workflows, Queues und Persistenz

[Übergeordnete Kategorie: Webframeworks und KI-Framework-SDKs](../web-ki-integration.md)

Nicht alle KI-gestützten Aufgaben eignen sich für eine direkte synchrone HTTP-Antwort. Komplexe Agenten-Workflows, mehrstufige Dokumentenanalysen oder die Generierung von Vektoreinbettungen für große Datenbestände beanspruchen oft Minuten. Werden solche Aufgaben direkt in einem HTTP-Request ausgeführt, führen vorgeschaltete Reverse Proxies oder API-Gateways nach 30 bis 60 Sekunden zu unvermeidbaren Gateway-Timeouts (HTTP 504).

---

## Das Worker- und Warteschlangen-Muster

Um Webserver-Threads von langlaufenden Modellprozessen freizuhalten, wird die Ausführung über eine Nachrichten-Warteschlange (Message Queue) entkoppelt:

```
[Browser / Client]
       │ 1. POST /api/analysis
       ▼
[Webframework Controller]
       │ 2. Job-ID erzeugen & Auftrag in Queue ablegen
       ├──────────────────────────────────────────────┐
       │ 3. 202 Accepted { "job_id": "xyz123" }       │
       ▼                                              ▼
[Client fragt Status ab]                    [Job-Queue (Redis/RabbitMQ)]
       │                                              │ 4. Task abholen
       │                                              ▼
       │                                    [Hintergrund-Worker]
       │                                       ├─ KI-SDK aufrufen
       │                                       └─ RAG-Pipeline ausführen
       │                                              │ 5. Ergebnis speichern
       │                                              ▼
       └─────────────────────────────────────► [PostgreSQL-Datenbank]
```

### Die drei Phasen des Ablaufs:
1. **Auftragsannahme (Ingestion):** Der Webserver prüft die Authentifizierung, validiert die Eingabedaten und schreibt den Arbeitsauftrag in die Queue (z. B. über Celery in Python oder BullMQ in Node.js). Er antwortet dem Client sofort mit dem HTTP-Statuscode `202 Accepted` und liefert die generierte `job_id` sowie eine URL zur Statusabfrage zurück.
2. **Asynchrone Verarbeitung (Execution):** Ein separater Hintergrund-Worker entnimmt den Auftrag der Queue, initialisiert das KI-Framework-SDK und führt die Inferenz- oder Analyseschritte durch. Der Webserver bleibt währenddessen für andere Anfragen voll einsatzbereit.
3. **Ergebnisabruf (Retrieval):** Nach Abschluss schreibt der Worker das Ergebnis in die Datenbank. Der Client erfährt vom Abschluss entweder über periodisches Polling der Status-URL oder über ein ereignisgesteuertes Signal (SSE oder WebSocket).

---

## Persistenzstrategie in PostgreSQL

In einer sauberen Architektur übernimmt PostgreSQL drei getrennte Speicherrollen:

1. **Relationale Anwendungsdaten:** Speicherung von Benutzern, Organisationen, Rollen (RBAC), Auftragsstatus und Kostenprotokollen in normalen Tabellen mit Fremdschlüsselbeziehungen.
2. **Semantischer Vektorspeicher (`pgvector`):** Speicherung von Textfragmenten (Chunks), ihren zugehörigen Einbettungsvektoren und Metadaten zur Realisierung semantischer Suchen.
3. **Agenten-Checkpoints und Sitzungsverläufe:** Serialisierte Zustände (z. B. der Message-Graph bei LangGraph), die es ermöglichen, mehrstufige Agenten nach einem Schritt zu pausieren und später exakt an diesem Zustand fortzusetzen.

---

## Vermeidung von Connection-Pool-Erschöpfung

Ein häufiger und schwerwiegender Architekturfehler bei der Anbindung von KI-SDKs in Webanwendungen ist das **Offenhalten von Datenbanktransaktionen während der Modell-Inferenz**.

* **Problem:** Da Sprachmodelle eine variable Antwortzeit von mehreren Sekunden besitzen, blockiert ein Thread während dieser Zeit eine Verbindung aus dem Datenbank-Verbindungspool (z. B. PgBouncer, SQLAlchemy Pool oder HikariCP). Bereits wenige Dutzend parallele Anfragen führen dazu, dass der Pool erschöpft ist. Reguläre Web-Anfragen für einfache Seitenaufrufe blockieren und die gesamte Webanwendung fällt aus, obwohl die Datenbank selbst kaum CPU-Last verzeichnet.
* **Architekturregel:** Modellaufrufe müssen stets **außerhalb aktiver Datenbanktransaktionen** stattfinden:
  1. Daten für den Kontext aus der Datenbank lesen und Transaktion sofort schließen.
  2. Inferenz über das KI-SDK durchführen (keine offene DB-Verbindung).
  3. Neue Transaktion öffnen, Ergebnis in die Datenbank schreiben und sofort committen.

---

> [!NOTE]
> Wenn das Modell im Rahmen dieser Workflows externe Funktionen oder Datenänderungen anstoßen soll, sind besondere Sicherheitsvorkehrungen nötig. Diese werden im Abschnitt [Sichere Werkzeugausführung und Sandboxing](tool-sandboxing.md) behandelt.
