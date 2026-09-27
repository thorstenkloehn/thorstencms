# Webframeworks und KI-Framework-SDKs

Das Zusammenspiel moderner Webframeworks mit spezialisierten KI-Framework-SDKs bildet das architektonische Fundament zeitgemäßer KI-Anwendungen. Während Webframeworks den verlässlichen Rahmen für HTTP-Routing, Sicherheit, Authentifizierung und Datenbanktransaktionen bereitstellen, kapseln KI-SDKs den Zugriff auf Inferenz-Endpunkte, Vektormodelle und Agentenlogik.

Die zentrale architektonische Herausforderung liegt im Aufeinandertreffen zweier gegensätzlicher Paradigmen:

* **Klassische Webarchitekturen** basieren auf kurzlebigen, zustandslosen Request-Response-Zyklen. Controller erwarten Antworten innerhalb von Millisekunden bis wenigen Sekunden, um Web-Worker schnell für neue Anfragen freizugeben.
* **Sprachmodelle und Agenten-Frameworks** arbeiten hingegen mit variabler Latenz, kontinuierlichen Token-Datenströmen oder mehrstufigen Denkprozessen, die Sekunden oder gar Minuten beanspruchen können.

```
┌─────────────────────────────────────────────────────────────┐
│                      Client / Frontend                      │
└──────────────────────────────▲──────────────────────────────┘
                               │ HTTP / SSE / WebStreams
┌──────────────────────────────▼──────────────────────────────┐
│ Webframework (FastAPI, Django, Next.js, Spring Boot, etc.)   │
│  ├─ Controller / Routing (HTTP-Endpunkte, Session, Auth)     │
│  ├─ Sicherheitsgrenze (RBAC, Rate Limiting, Input Sanitize) │
│  └─ Protokoll-Adapter (SSE-Streaming, Background-Dispatch)  │
└──────────────────────────────▲──────────────────────────────┘
                               │ Typsichere Methodenaufrufe
┌──────────────────────────────▼──────────────────────────────┐
│ KI-Framework-SDK (Provider-SDK, Fullstack-SDK, Agent-Graph) │
│  ├─ Token-Generierung & Streaming-Schnittstellen             │
│  ├─ Kontext-Orchestrierung & Retrieval (RAG)                │
│  └─ Strukturierte Vorschläge für Werkzeugaufrufe            │
└──────────────────────────────▲──────────────────────────────┘
                               │ SQL / pgvector
┌──────────────────────────────▼──────────────────────────────┐
│ Persistenzschicht: PostgreSQL (Relationen, Vektoren, State) │
└─────────────────────────────────────────────────────────────┘
```

---

## Kernaufgaben der Schichtentrennung

Um robuste, skalierbare und sichere Systeme zu bauen, dürfen KI-SDKs niemals ungefiltert an den HTTP-Client exponiert werden. Das Webframework übernimmt als Schutzschicht vier unverzichtbare Aufgaben:

1. **Autorisierung und Mandantenfähigkeit:** Ein Sprachmodell besitzt von sich aus kein Konzept von Benutzerrechten. Das Webframework muss sicherstellen, dass dem Modell ausschließlich Daten übergeben werden, auf die der anfragende Benutzer Zugriff hat.
2. **Entkopplung langer Laufzeiten:** Blockierende Aufrufe müssen entweder über Streaming schrittweise sichtbar gemacht oder über asynchrone Warteschlangen aus dem synchronen Web-Thread ausgelagert werden.
3. **Validierung und Sandboxing:** Vom Modell vorgeschlagene Funktionsaufrufe (Function Calling) müssen strikt typisiert und vor der Ausführung autorisiert werden.
4. **Schutz der Datenverbindung:** Datenbanktransaktionen dürfen nicht über langanhaltende Modellaufrufe hinweg offen gehalten werden, um eine Erschöpfung des Verbindungspools (Connection Pool Exhaustion) zu vermeiden.

---

## Unterkategorien dieses Kapitels

Die folgenden Abschnitte vertiefen die technischen Umsetzungsdetails dieser Architektur:

* [Streaming und Transportprotokolle](web-ki-integration/streaming-transport.md): Latenzarmes Ausliefern generierter Tokens über Server-Sent Events, WebSockets und Web Streams sowie die Behandlung von Client-Abbrüchen.
* [Asynchrone Workflows, Queues und Persistenz](web-ki-integration/workflows-persistenz.md): Entkopplung langlaufender Agentenprozesse mittels Job-Queues, Session-Checkpointing und getrennte Speicherpfade in PostgreSQL.
* [Sichere Werkzeugausführung und Sandboxing](web-ki-integration/tool-sandboxing.md): Absicherung von Tool-Calling-Mechanismen, Schemavalidierung und Human-in-the-Loop-Freigaben zum Schutz vor Prompt-Injection.

---

> [!NOTE]
> Die Einordnung konkreter Modellanbindungen und Bibliotheken findet sich in den Abschnitten [Sprachmodelle in Webframeworks & Backend](sprachmodelle/frameworks.md) und [KI-Integrations- und Modellbibliotheken](sprachmodelle/bibliotheken.md).
