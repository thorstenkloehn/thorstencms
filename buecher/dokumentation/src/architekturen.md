# Architekturen im Zusammenhang

Digitale Informationssysteme existieren selten als isolierte Monolithen. In modernen Organisationen greifen unterschiedliche Architekturmodelle ineinander: Technische Handbücher entstehen über dateibasierte Docs-as-Code-Pipelines, Marketing- und Produktinhalte werden in Content-Management-Systemen redaktionell gepflegt, internes Unternehmenswissen wird in semantischen Wissensgraphen verknüpft, und Schulungsmaterialien werden über Lernmanagement-Systeme bereitgestellt.

Die Integration von Sprachmodellen und KI-Framework-SDKs verbindet diese ehemals getrennten Welten zu einem kohärenten Gesamtsystem. Dieses Kapitel führt die Perspektiven des Buches zusammen und liefert einen ganzheitlichen Architekturüberblick.

---

## Die Gesamtarchitektur im Zusammenspiel

Das folgende Schichtenmodell veranschaulicht, wie die in den Einzelkapiteln behandelten Bausteine über standardisierte Protokolle (wie MCP, SSE, REST und LTI) interagieren:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                             Client- & Autorenebene                          │
│  ├─ Web-Browser (SSE / Streams)        ├─ Mobile / Desktop-Apps (Local-First)│
│  ├─ IDEs & Editoren (LSP / Inline-Diff)├─ Autorentools (Track Changes / FIM)│
└──────────────────────────────────────┬──────────────────────────────────────┘
                                       │ Protokolle (HTTP, SSE, LTI 1.3, WebSockets)
┌──────────────────────────────────────▼──────────────────────────────────────┐
│                    Anwendungs- & Orchestrierungs-Schicht                    │
│  ├─ Webframework-Backend (FastAPI, Django, Spring Boot, ASP.NET Core)       │
│  ├─ CMS-Redaktionsengine & Workflow-Staging (Draft -> Review -> Published)  │
│  ├─ LMS-Lernservice mit didaktischen Schutzplanken (Sokratischer Tutor)     │
│  └─ Multi-Agenten-Orchestrierung (LangGraph-Zustandsgraphen mit Interrupts) │
└──────────────────────────────────────┬──────────────────────────────────────┘
                                       │ Model Context Protocol (MCP) / JSON-RPC
┌──────────────────────────────────────▼──────────────────────────────────────┐
│                  Standardisierte Werkzeug- & Gateway-Ebene                  │
│  ├─ LiteLLM Gateway (Multi-Provider-Routing, Fallbacks & Kostenkontrolle)   │
│  ├─ Lokale Inferenz-Engines (Ollama, CoreML, ExecuTorch, WebGPU)            │
│  └─ MCP-Server (Dateisysteme, Git-Repositories, externe APIs)               │
└──────────────────────────────────────┬──────────────────────────────────────┘
                                       │ SQL / Relationen / Vektoren / Git
┌──────────────────────────────────────▼──────────────────────────────────────┐
│                   Persistenz- & Single-Source-of-Truth-Ebene                │
│  ├─ PostgreSQL & pgvector (Relationale Daten, Vektoren, Checkpoints)        │
│  ├─ Git-Repositories (Markdown, AsciiDoc, Quellcode, Revisions-Deltas)      │
│  └─ Lokale SQLite-Datenbanken (`sqlite-vec` & CRDTs auf Mobilgeräten)       │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Vergleichende Domänen-Matrix

Jede behandelte Architekturdomäne erfüllt eine spezifische didaktische und technische Funktion innerhalb des Gesamtsystems:

| Domäne | Primärer Speicherweg | Leitfrage der Domäne | Spezifische Rolle des KI-SDKs | Primärer Schutzmechanismus |
| :--- | :--- | :--- | :--- | :--- |
| **[Wissenssysteme](wissenssysteme-ki-integration.md)** | PostgreSQL / `pgvector` | Wie finden und verknüpfen Menschen Wissen? | Hybrides Retrieval (BM25 + Vektoren), Re-Ranking, Zitationslogik | SQL Pre-Filtering (`WHERE acl_groups && :roles`) |
| **[CMS](cms-ki-integration.md)** | PostgreSQL (Relationen & Entwürfe) | Wie werden Inhalte redaktionell gepflegt? | Structured Outputs für Content-Modelle, Taxonomien, Alt-Texte | Drei-Stufen-Staging (`AI Draft` ➔ `Review` ➔ `Published`) |
| **[Docs-as-Code](docs-as-code-ki-integration.md)** | Git-Repository (Markdown / Text) | Wie werden Änderungen nachvollziehbar gebaut? | Pull-Request-Automatisierung, Drift-Erkennung, Code-to-Docs | Deterministische CI-Linter-Schleifen (`mdbook`, `vale`) |
| **[Webframeworks](web-ki-integration.md)** | PostgreSQL (Transaktionen) | Wie werden Daten zuverlässig ausgeliefert? | Asynchrones Token-Streaming (SSE), Background-Worker-Queues | Tool-Execution-Sandbox, Connection-Pool-Schutz |
| **[LMS](lms-ki-integration.md)** | PostgreSQL & LRS (xAPI) | Wie wird nachhaltiges Verstehen gefördert? | Sokratischer Tutor (Scaffolding), interaktive Übungen | Didaktische Guardrails, Verbot autonomer Benotung |
| **[Autorentools](autorentools-ki-integration.md)** | Lokale Dateien (DOCX, ODT, MD) | Wie wird der Schreib- und Denkprozess gestützt? | In-line-Vervollständigung (FIM), Ghost-Text, Stilprüfung | Native Änderungsverfolgung (Track Changes), Manuskriptschutz |
| **[IDEs & Editoren](ide-ki-integration.md)** | Projekt-Workspace / Git | Wie wird Code präzise entwickelt und getestet? | LSP-Kontextanalyse, AST-Patching, TDD-Testschleifen | Workspace Trust, Terminal-Whitelisting, Code-Skelette |
| **[Apps (Mobile/Desktop)](apps-ki-integration.md)** | Lokale SQLite (`sqlite-vec`) | Wie funktioniert Software offline und mobil? | On-Device-Inferenz (CoreML, ExecuTorch), Offline-RAG | Asymmetrisches Hybrid-Routing, Battery Guard |
| **[Multi-Agenten](multi-agenten-ki-integration.md)** | PostgreSQL (`checkpoints`) | Wie lösen vernetzte Spezialisten Großaufgaben? | Supervisor-Planung, Werkzeugaufrufe über offene MCP-Server | Relationales Checkpointing, Time-Travel, Interrupts |

---

## Vier fundamentale Architekturentscheidungen

Bei der Konzeption eines Gesamtsystems müssen Architekten vier grundlegende Weichenstellungen treffen:

### 1. Inferenz-Topologie: Edge (On-Device) vs. Cloud-Gateway
* **On-Device (Local-First):** Unerlässlich bei sensiblen Manuskripten in [Autorentools](autorentools-ki-integration/datensouveraenitaet-lokale-modelle.md) und mobilen Apps ohne Netzempfang ([Mobile Apps](apps-ki-integration/on-device-hardwarebeschleunigung.md)). Nutzt quantisierte 4-Bit-Modelle auf lokalen NPUs.
* **Zentrales Cloud-Gateway:** Erforderlich für unternehmensweite RAG-Pipelines in [Wissenssystemen](wissenssysteme-ki-integration/hybrid-retrieval-reranking.md) oder speicherintensive Agentengraphen. Nutzt [LiteLLM](sprachmodelle/bibliotheken.md) für Ausfallsicherheit und Kostenkontrolle.

### 2. Persistenz und Konsistenz: Git vs. Relationale Datenbanken
* **Git-basiert:** Der ideale Speicherort für textuelle Quellbestände, Dokumentationen ([Docs-as-Code](docs-as-code-ki-integration/git-pr-automation.md)) und Programmcode ([IDEs](ide-ki-integration/inline-diff-patching.md)). Bietet kryptografische Integrität und zeilenbasierte Diffs.
* **PostgreSQL-basiert:** Der unverzichtbare Speicherort für transaktionale Workflows, relationale Redaktionszustände ([CMS](cms-ki-integration/redaktionelle-workflows-freigabe.md)), semantische Vektoreinbettungen (`pgvector`) und Agenten-Checkpoints ([Multi-Agenten](multi-agenten-ki-integration/zustandsgraphen-human-in-the-loop.md)).

### 3. Transport und Kopplung: Synchron vs. Asynchron
* **Synchrones Streaming (SSE):** Standard für unmittelbares menschliches Feedback bei Chat-Interaktionen und In-Editor-Generierungen ([Webframeworks](web-ki-integration/streaming-transport.md)).
* **Asynchrone Event-Entkopplung (Queues & Webhooks):** Zwingend erforderlich für langlaufende Agenten-Recherchen, mehrsprachige Übersetzungen in Headless-CMS ([CMS](cms-ki-integration/headless-webhooks-automation.md)) und CI/CD-Linter-Schleifen ([Docs-as-Code](docs-as-code-ki-integration/ci-cd-linter-schleifen.md)), um HTTP-Timeouts zu verhindern.

### 4. Governance und die Rolle des Menschen (Human-in-the-Loop)
Unabhängig von der Domäne gilt das eiserne architektonische Prinzip: **Keine autonome Aktion mit Außenwirkung ohne menschliche Validierungsgrenze.**
* Im **CMS** verhindert das Staging-Modell automatische Veröffentlichungen.
* Im **Docs-as-Code** erzwingt der Pull Request die Begutachtung durch Maintainer.
* Im **LMS** schützen didaktische Guardrails vor unzulässigen KI-Prüfungsnoten.
* In der **IDE** schützen Workspace-Trust-Richtlinien vor gefährlichen Terminalbefehlen.
* In **Multi-Agenten-Systemen** halten programmatische Interrupts den Zustandsgraphen vor kritischen Operationen an.

---

> [!NOTE]
> Die Kriterien zur Auswahl der zugrundeliegenden Softwarebausteine und deren Reifegrade sind im Kapitel [Softwareauswahl und Reifegrade](software.md) dokumentiert.
