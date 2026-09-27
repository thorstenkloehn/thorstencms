# Sprachmodelle in Webframeworks & Backend

[Übergeordnete Kategorie: Integration von Sprachmodellen in Software-Architekturen](../sprachmodell-integration.md)

Modellanbindung auf Service- und Controller-Ebene, Token-Streaming (SSE), sichere Werkzeugausführung (Tool Calling) und Datenbankspeicherung.

## Integrationsarchitektur: Webframework und KI-Laufzeit

Ein Webframework ist für den HTTP-Lebenszyklus, Authentifizierung, Autorisierung (RBAC), Eingabevalidierung und Datenbanktransaktionen zuständig. KI-Frameworks oder Modell-SDKs steuern hingegen Prompts, Modellinferenz, Einbettungen und RAG-Pipelines. Die Kopplung beider Welten erfordert eine klare Schichtentrennung:

```
┌─────────────────────────────────────────────────────────────┐
│                      Client / Browser                       │
└──────────────────────────────▲──────────────────────────────┘
                               │ HTTP / SSE (Event Stream)
┌──────────────────────────────▼──────────────────────────────┐
│ Webframework-Backend (Controller / Middleware)               │
│  ├─ Authentifizierung & Session-Validierung                  │
│  ├─ Ratenbegrenzung & Eingabe-Sanitizing (Pydantic / Zod)   │
│  └─ Asynchrones Streaming oder Dispatch an Job-Queue        │
└──────────────────────────────▲──────────────────────────────┘
                               │ Interne Methodenaufrufe
┌──────────────────────────────▼──────────────────────────────┐
│ Service-Schicht (KI-Framework / Modell-SDK)                 │
│  ├─ Prompt-Zusammenstellung & Modell-Inferenz               │
│  ├─ RAG-Logik (Retrieval & Kontextbegrenzung)               │
│  └─ Strukturierte Vorschläge für Werkzeugaufrufe            │
└──────────────────────────────▲──────────────────────────────┘
                               │ SQL / pgvector
┌──────────────────────────────▼──────────────────────────────┐
│ Persistenz: PostgreSQL (Relationale Daten, Vektoren, Logs) │
└─────────────────────────────────────────────────────────────┘
```

---

## Vier Kernmuster der Integration

### 1. Token-Streaming über Server-Sent Events (SSE)
Für dialogorientierte Schnittstellen (Chat, interaktive Zusammenfassung) ist das blockierende Warten auf vollständige Antworten ungeeignet.
* **Protokollwahl:** Server-Sent Events (`text/event-stream`) bieten gegenüber WebSockets den Vorteil, dass sie auf Standard-HTTP/1.1 oder HTTP/2 aufsetzen, zustandslose Proxies passieren und automatische Wiederverbindungsmechanismen mitbringen.
* **Umsetzung:** Der Controller ruft die asynchrone Stream-Schnittstelle des KI-Frameworks oder SDKs auf (`async for` bzw. reaktive Streams) und gibt jeden generierten Token-Chunk unmittelbar im HTTP-Ausgabestrom an den Client weiter.

### 2. Entkopplung über Hintergrund-Warteschlangen (Worker-Pattern)
Komplexe Agenten-Workflows, mehrstufige Recherchen oder die Indizierung umfangreicher Dokumentenmengen übersteigen reguläre HTTP-Request-Timeouts (häufig 30 bis 60 Sekunden).
* **Entkopplung:** Der Webserver nimmt den Auftrag entgegen, speichert die Metadaten in PostgreSQL und übergibt die Ausführung an eine nachgelagerte Task-Queue (z. B. Celery, BullMQ oder ein In-Memory-Warteschlangensystem).
* **Rückmeldung:** Der HTTP-Endpunkt antwortet unmittelbar mit `202 Accepted` und einer Auftrags-ID. Das Frontend erfährt den Fortschritt über Polling, WebSocket-Events oder SSE-Statusbenachrichtigungen.

### 3. Sichere Werkzeugausführung (Tool Calling Sandbox)
Sprachmodelle führen Aktionen nicht selbst aus; sie formulieren lediglich den strukturierten Vorschlag für einen Funktionsaufruf (JSON mit Argumenten).
* **Schutzmechanismen:** Das Webframework muss diesen Vorschlag vor der Ausführung isolieren.
* **Validierung:** Prüfung der übergebenen Argumente gegen ein striktes Typenschema (z. B. Pydantic, Zod oder JSON-Schema).
* **Rechteprüfung:** Sicherstellung, dass der aktuell angemeldete Benutzer über die nötigen Rollenberechtigungen für die angeforderte Aktion verfügt.
* **Fehlerbehandlung:** Fehlschläge oder ungültige Parameter werden als strukturierte Fehlermeldung an das Modell zurückgespielt, damit es den Aufruf korrigieren kann.

### 4. Getrennte Persistenz und Vektorspeicher
Die Datenhaltung teilt sich in drei funktionale Bereiche auf, die sich in PostgreSQL abbilden lassen:
* **Transaktionale Anwendungsdaten:** Benutzerprofile, Berechtigungen und Abrechnungsdaten in relationalen Standardtabellen.
* **Semantische Einbettungen:** Dokumenten-Chunks und Vektordaten über die Erweiterung `pgvector`.
* **Konversations- und Agentenzustand:** Serialisierte Sitzungsverläufe und Zwischenzustände (Checkpoints) für unterbrochene oder mehrstufige Arbeitsabläufe.

---

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | [ASP.NET Core](https://github.com/dotnet/aspnetcore) | MIT | Sehr hoch | Webframework-Kern; Modellaufrufe in eigener Anwendung ergänzen. | PostgreSQL: [EF Core mit Npgsql](https://www.npgsql.org/efcore/) |
| 2 | [Django](https://github.com/django/django) | BSD-3-Clause | Sehr hoch | Webframework-Kern mit ORM; Modell- und Vektoranbindung zusätzlich entwickeln. | PostgreSQL: [Offizielles PostgreSQL-Backend](https://docs.djangoproject.com/en/stable/ref/databases/#postgresql-notes) |
| 3 | [FastAPI](https://github.com/fastapi/fastapi) | MIT | Sehr hoch | Asynchrones Python-API-Framework für latenzarmes Token-Streaming und Modell-Gateways. | PostgreSQL: [Eigene SQLAlchemy-Anbindung über PostgreSQL-Dialekt](https://docs.sqlalchemy.org/en/20/dialects/postgresql.html) |
| 4 | [Symfony](https://github.com/symfony/symfony) | MIT | Sehr hoch | PHP-Webframework; Modellaufrufe in eigenen Diensten ergänzen. | PostgreSQL: [Doctrine und PostgreSQL-Anbindung](https://symfony.com/doc/current/doctrine.html) |
| 5 | [Spring Boot](https://github.com/spring-projects/spring-boot) / [Spring AI](https://github.com/spring-projects/spring-ai) | Apache-2.0 | Hoch | Dokumentierte Java-Abstraktion für Chat-Clients, Prompt-Templates und pgvector-Stores. | PostgreSQL: [pgvector-Integration via Spring AI](https://docs.spring.io/spring-ai/reference/api/vectordbs/pgvector.html) |

---

## Einsatz und Abgrenzung der Frameworks

Die Tabelle unterscheidet den Webframework-Kern von einer selbst entwickelten Modellanbindung. Bei Spring AI ist eine konkrete KI-Bibliothek benannt; bei den übrigen Frameworks müssen Modellaufruf, Fehlerbehandlung und Berechtigungen in der Anwendung ergänzt werden:

- **ASP.NET Core:** Erlaubt über Minimal APIs und `IAsyncEnumerable<T>` ein direktes Token-Streaming. Für die Modellanbindung kann Microsoft Semantic Kernel oder ein dediziertes Provider-SDK genutzt werden. Persistenz erfolgt über Entity Framework Core mit dem Npgsql-Treiber.
- **Django:** Traditionell synchron aufgebaut, bietet aber mit Channels und asynchronen Views Anknüpfungspunkte für Modell-Streams. Für aufwendige KI-Workflows empfiehlt sich die Auslagerung an Celery-Worker. Vektoren lassen sich über `pgvector-python` in Django-Modelle einbinden.
- **FastAPI:** Nativ asynchron konzipiert auf Basis von Starlette und Pydantic. Eignet sich durch minimale Overhead-Latenz und asynchrone Generatoren (`StreamingResponse`) optimal als API-Gateway vor Python-basierten Frameworks wie LangGraph oder LlamaIndex.
- **Symfony:** Ermöglicht über den Symfony HttpClient und den Messenger-Bus eine klare Trennung zwischen synchroner HTTP-Auslieferung und asynchroner Worker-Verarbeitung von KI-Aufträgen. Daten und Vektor-Metadaten werden über Doctrine ORM in PostgreSQL verwaltet.
- **Spring Boot / Spring AI:** Bietet eine integrierte Java-Abstraktionsschicht für Chat-Clients, Embedding-Modelle und Vektorspeicher. Das reaktive Modul (WebFlux) unterstützt gestreamte HTTP-Antworten über `Flux<ServerSentEvent>`.

Zu den zugrunde liegenden Modellbibliotheken, Provider-SDKs und Gateways siehe [KI-Integrations- und Modellbibliotheken](bibliotheken.md). Weiterführende Details zu autonomen Coding-Agenten finden sich unter [KI-native Bausteine und agentengestützte Entwicklung](../webframeworks/ki-agenten.md).
