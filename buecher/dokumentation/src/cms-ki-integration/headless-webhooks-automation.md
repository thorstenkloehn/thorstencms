# Headless-Architekturen, Webhooks und Event-Pipelines

[Übergeordnete Kategorie: Content-Management-Systeme und KI-Framework-SDKs](../cms-ki-integration.md)

In modernen Webarchitekturen setzen Unternehmen zunehmend auf Headless- oder Composable-CMS-Systeme. Bei diesen Systemen ist die Inhaltsverwaltung (Authoring) vollständig von der Präsentationsschicht (Frontend) entkoppelt; der Datenaustausch erfolgt über strukturierte REST- oder GraphQL-Schnittstellen. Für die Integration von KI-Framework-SDKs eröffnen Headless-Architekturen die Möglichkeit, Content-Veredelungsprozesse über ereignisgesteuerte Hintergrund-Pipelines (Webhooks) abzubilden.

---

## Die event-getriebene Content-Veredelungspipeline

Anstatt Redakteure im Editor durch blockierende KI-Generierungsdialoge aufzuhalten, werden zeitintensive Aufgaben (wie automatische Übersetzungen, Textzusammenfassungen oder Medienanalysen) asynchron über Webhooks ausgeführt:

```
[Redakteur speichert Roh-Artikel im CMS]
                   │ Event: entry.create / draft_saved
                   ▼
┌─────────────────────────────────────────────────────────────┐
│ 1. CMS-Backend feuert Webhook                               │
│    Payload: { "entry_id": 412, "locale": "de", "title": ...}│
└──────────────────────────────┬──────────────────────────────┘
                               │ HTTP POST an Microservice
┌──────────────────────────────▼──────────────────────────────┐
│ 2. Entkoppelter KI-Veredelungsdienst                        │
│    ├─ Task in Worker-Queue (BullMQ / Celery) einreihen      │
│    ├─ KI-SDK aufrufen: Übersetzung in EN, ES, FR            │
│    └─ KI-SDK aufrufen: Generierung von Teaser & SEO-Tags    │
└──────────────────────────────┬──────────────────────────────┘
                               │ REST / GraphQL Mutation
┌──────────────────────────────▼──────────────────────────────┐
│ 3. Rückschreiben ins CMS                                    │
│    Schreibt Ergebnisse in Entwurfsfelder der Zielsprachen   │
└──────────────────────────────┬──────────────────────────────┘
                               │ WebSocket / UI-Event
┌──────────────────────────────▼──────────────────────────────┐
│ 4. Redaktions-UI aktualisiert Ansicht                       │
│    Redakteur erhält Meldung: "Übersetzungen bereit zur Sicht"│
└─────────────────────────────────────────────────────────────┘
```

### Vorteile der Webhook-Entkopplung:
* **Keine Latenz im Redaktionsalltag:** Der Redakteur kann nach dem Speichern sofort an einem anderen Artikel weiterarbeiten.
* **Skalierbarkeit und Retry-Mechanismen:** Fällt ein externer Modell-Provider temporär aus (z. B. HTTP 503 oder Rate Limits), fängt die Warteschlange des Veredelungsdienstes den Fehler ab und wiederholt den Versuch nach einer Wartezeit (Exponential Backoff), ohne dass Daten im CMS verloren gehen.
* **Technologiefreiheit:** Der KI-Dienst kann in Python (z. B. mit FastAPI und LangGraph) betrieben werden, selbst wenn das CMS selbst auf Node.js oder PHP basiert.

---

## Strikte Trennung von Inferenz und Auslieferung (Delivery Layer)

Ein elementarer Grundsatz für hochverfügbare Webanwendungen lautet: **Keine Live-Modell-Inferenz im regulären Seitenaufruf für Endbesucher.**

* **Das Performance- und Kostenrisiko:** Würde ein Webserver bei jedem Aufruf eines Blogartikels ein KI-SDK anfragen, um dynamische Zusammenfassungen oder personalisierte Teaser zu generieren, stiege die Ladezeit (Time to First Byte / TTFB) von wenigen Millisekunden auf mehrere Sekunden. Zudem würden Tausende gleichzeitiger Besucher das Budget für API-Token innerhalb kürzester Zeit aufbrauchen.
* **Die Architekturlösung:** Alle KI-gestützten Veredelungsschritte müssen **zum Redaktionszeitpunkt (Build- oder Save-Time)** erfolgen. Die fertigen Texte und Metadaten werden in der PostgreSQL-Datenbank des CMS gespeichert und anschließend als statische HTML-Seiten (SSG) oder über Content Delivery Networks (CDNs) mit kurzen Latenzzeiten an die Besucher ausgeliefert.

---

> [!NOTE]
> Details zum Aufbau asynchroner Warteschlangen und Worker-Prozesse finden sich im Kapitel [Webframeworks und KI-Framework-SDKs](web-ki-integration/workflows-persistenz.md).
