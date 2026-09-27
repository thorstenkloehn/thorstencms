# Multi-Agenten-Systeme und Protokolle

Einzelne Sprachmodell-Aufrufe stoßen bei vielschichtigen Aufgabenstellungen an fundamentale Grenzen: Ein einzelner Prompt kann nicht gleichzeitig tiefgreifende Recherchen durchführen, komplexe Systemarchitekturen entwerfen, Quellcode schreiben und kritische Sicherheitsprüfungen vornehmen, ohne den Überblick zu verlieren oder wesentliche Details zu übersehen.

Moderne KI-Architekturen setzen daher auf **Multi-Agenten-Systeme**: Mehrere spezialisierte Agenteninstanzen mit klar abgegrenzten Rollen, Werkzeugen und System-Prompts arbeiten koordiniert zusammen, um übergeordnete Ziele zu erreichen.

Die Beherrschung von Multi-Agenten-Systemen erfordert zwei grundlegende Bausteine:

* **Offene Protokollstandards (Model Context Protocol / MCP):** Anstatt für jedes Werkzeug und jede Datenbank proprietäre APIs zu schreiben, standardisiert MCP die Bereitstellung von Kontextdaten, Ressourcen und ausführbaren Funktionen zwischen Host-Anwendungen und Agenten.
* **Deterministische Orchestrierung:** Agenten dürfen nicht unkontrolliert in chaotischen Gesprächsschleifen verharren. Frameworks wie LangGraph, AutoGen oder CrewAI strukturieren die Interaktion über definierte Rollen, hierarchische Supervisor-Muster oder zyklische Zustandsgraphen.

```
┌─────────────────────────────────────────────────────────────┐
│                 Benutzer / Steuernde Anwendung              │
└──────────────────────────────▲──────────────────────────────┘
                               │ Zielvorgabe & Freigaben
┌──────────────────────────────▼──────────────────────────────┐
│ Orchestrierungsschicht (LangGraph / AutoGen / Supervisor)   │
│  ├─ Aufgaben-Zerlegung & Delegation an Spezialisten         │
│  ├─ Zustandsverwaltung (Graph-State) & Checkpointing        │
│  └─ Human-in-the-Loop-Unterbrechungen bei kritischen Toren  │
└──────┬───────────────────────┼───────────────────────┬──────┘
       │                       │                       │
       ▼                       ▼                       ▼
┌──────────────┐        ┌──────────────┐        ┌──────────────┐
│ Recherche-   │        │ Entwicklungs-│        │ Review- &    │
│ Agent        │        │ Agent        │        │ QA-Agent     │
└──────┬───────┘        └──────┬───────┘        └──────┬───────┘
       │                       │                       │
       └───────────────────────┼───────────────────────┘
                               │ Standardisierte Tool-Aufrufe (MCP)
┌──────────────────────────────▼──────────────────────────────┐
│ Model Context Protocol (MCP) Server-Schicht                 │
│  ├─ MCP-Server Dateisystem (stdio)                          │
│  ├─ MCP-Server PostgreSQL / pgvector (SSE)                  │
│  └─ MCP-Server Git / GitHub API                             │
└─────────────────────────────────────────────────────────────┘
```

---

## Kernaufgaben der Multi-Agenten-Architektur

1. **Rollen-Spezialisierung:** Jeder Agent besitzt ein eng umrissenes Aufgabenprofil (z. B. Rechercheur, Programmierer, Sicherheitsprüfer) und hat ausschließlich Zugriff auf jene Werkzeuge, die für seine Rolle zwingend nötig sind.
2. **Standardisierte Kontextkopplung:** Über das Model Context Protocol werden Werkzeuge und Datenquellen modular entkoppelt. Ein MCP-Server für PostgreSQL kann unverändert von unterschiedlichen Agenten-Frameworks genutzt werden.
3. **Fehlertoleranz und Persistenz:** Scheitert ein Agent an einem Teilschritt, muss das Gesamtsystem in der Lage sein, den Zustand zurückzuspulen (Time-Travel), alternative Lösungswege zu testen oder die menschliche Aufsicht zu Rate zu ziehen.

---

## Unterkategorien dieses Kapitels

Die konkreten Implementierungsmuster gliedern sich in drei Schwerpunkte:

* [Das Model Context Protocol (MCP) und Schnittstellenstandards](multi-agenten-ki-integration/mcp-protokoll-standards.md): Architektur von MCP (Clients, Server, stdio/SSE-Transport) und die Kernprimitiven Prompts, Resources und Tools.
* [Agenten-Topologien, Koordination und Rollenmodelle](multi-agenten-ki-integration/topologien-orchestrierung.md): Gegenüberstellung von hierarchischen Supervisor-Systemen, konversationsbasierten Gruppen und deterministischen Zustandsgraphen.
* [Persistente Zustandsgraphen, Time-Travel und Human-in-the-Loop](multi-agenten-ki-integration/zustandsgraphen-human-in-the-loop.md): Checkpointing in PostgreSQL, Unterbrechung kritischer Aktionen und Time-Travel-Debugging von Agenten-Trajektorien.

---

> [!NOTE]
> Die qualitative Einordnung graphbasierter Frameworks wie LangGraph findet sich im Kapitel [KI-Integrations- und Modellbibliotheken](sprachmodelle/bibliotheken.md) sowie unter [KI-native Bausteine und agentengestützte Entwicklung](webframeworks/ki-agenten.md).
