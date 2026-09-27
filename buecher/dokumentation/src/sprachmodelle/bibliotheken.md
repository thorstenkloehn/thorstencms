# KI-Integrations- und Modellbibliotheken

[Übergeordnete Kategorie: Integration von Sprachmodellen in Software-Architekturen](../sprachmodell-integration.md)

Abstraktionsbibliotheken, Frameworks, Provider-SDKs, Gateways und lokale Open-Weights-Laufzeiten.

## Architekturschichten: SDKs, Frameworks und Gateways

Bei der technischen Einbindung von Sprachmodellen in bestehende Software-Architekturen lassen sich vier funktionale Abstraktionsschichten unterscheiden:

```
┌─────────────────────────────────────────────────────────────┐
│  Orchestrierungs- & Agenten-Frameworks (LangChain, DSPy)    │  ▲ Hohe Abstraktion
├─────────────────────────────────────────────────────────────┤  │ (Workflows, RAG,
│  Daten- & Index-Frameworks (LlamaIndex)                     │  │  Graph-Zustände)
├─────────────────────────────────────────────────────────────┤  │
│  Fullstack- & Gateway-Schichten (LiteLLM, Vercel AI SDK)    │  │
├─────────────────────────────────────────────────────────────┤  │
│  Provider- & Laufzeit-SDKs (Google GenAI, OpenAI, Ollama)   │  ▼ Hardware- &
└─────────────────────────────────────────────────────────────┘    API-Nähe
```

### 1. Provider-SDKs (Basisschicht)
Provider-SDKs (Software Development Kits) binden die herstellerspezifischen HTTP- oder gRPC-Schnittstellen der Modellanbieter direkt ein.
- **Funktionsumfang:** Authentifizierung, Serialisierung von Parametern (wie Temperatur, Token-Limits und strukturierte JSON-Schemata), Behandlung von HTTP-Verbindungsabbrüchen und Auslesen von Server-Sent Events (SSE) beim Token-Streaming.
- **Vorteile:** Minimale Latenz, keine überflüssigen Abstraktionsschichten („Zero Overhead“) und unmittelbare Verfügbarkeit neuer Provider-Funktionen (etwa spezifische Caching-Parameter, multimodale Eingaben oder erweiterte Kontrollflags für Denkprozesse).
- **Grenzen:** Kein integriertes Zustandsmanagement über Konversationsgrenzen hinweg; Werkzeugaufrufe (Function Calling) und Vektoranbindungen müssen in der eigenen Anwendungslogik implementiert werden.

### 2. Fullstack- und Entwicklungs-SDKs
Fullstack-SDKs schlagen eine Brücke zwischen Frontend, serverseitiger Laufzeit und Modell.
- Sie vereinheitlichen Kommunikationsprotokolle für Web-UIs, bieten Streaming-Hilfen für Serverkomponenten und standardisieren die Typisierung von Werkzeugaufrufen.
- Ziel ist ein reduzierter Boilerplate-Code bei interaktiven Benutzeroberflächen, ohne zwingend ein komplexes Agenten-Framework betreiben zu müssen.

### 3. Orchestrierungs- und Agenten-Frameworks
Frameworks stellen übergeordnete Kontrollstrukturen, Pipeline-Definitionen und Zustandsmaschinen bereit.
- **Workflow-Steuerung:** Strukturieren mehrstufige Ausführungsketten (Chains) und zyklische Zustandsgraphen mit Verzweigungen, Rollbacks und Human-in-the-Loop-Prüfungen.
- **RAG-Integration:** Automatisieren das Laden, Zerlegen (Chunking), Einbetten und Indizieren von Dokumentenbeständen sowie den semantischen Abruf über Vektordatenbanken.
- **Architektonische Risiken:** Gefahr undurchsichtiger Abstraktionen („Leaky Abstractions“), erschwerte Fehlerdiagnose im Produktivbetrieb und Abhängigkeit von Release-Zyklen der Framework-Betreiber bei API-Änderungen der Modellhersteller.

### 4. Gateway- und Proxy-Laufzeiten
Gateways schalten sich als Vermittler zwischen die Anwendung und die Modellanbieter.
- **Funktionsumfang:** Entkopplung über standardisierte Schnittstellen, automatisches Failover bei Dienstausfällen, Ratenbegrenzung (Rate Limiting), Caching identischer Anfragen und zentrale Kostenkontrolle über virtuelle Schlüssel.

---

## Kriterien für die Architekturentscheidung

Die Wahl zwischen einem schlanken SDK und einem umfassenden Framework hängt von den funktionalen Anforderungen ab:

| Anforderungskriterium | Empfohlene Architekturschicht | Begründung |
| :--- | :--- | :--- |
| **Geringe Latenz & maximale Kontrolle** | Provider-SDK | Direkte Streaming-Verbindung ohne Zwischenschichten; minimale Abhängigkeiten. |
| **Interaktive Web- und Chat-UIs** | Fullstack-SDK / Web-Framework | Serverseitiges Token-Streaming und UI-Zustandssynchronisation ohne Framework-Ballast. |
| **Dokumentenzentrierte Suche (RAG)** | Daten-Framework (z. B. LlamaIndex) | Spezialisierte Indizierungs-, Parsing- und Re-Ranking-Pipelines beschleunigen den Aufbau. |
| **Zyklische Multi-Step-Workflows** | Graphbasiertes Framework (z. B. LangChain/LangGraph) | Zustandsbehaftete Graphen, Checkpointing und Verzweigungslogik für Agenten-Pipelines. |
| **Multi-Provider-Strategie & Ausfallsicherheit** | Gateway-Proxy (z. B. LiteLLM) | Zentrales Modell-Routing, Lastverteilung und Budgetüberwachung unabhängig vom Anwendungscode. |
| **Systematische Prompt-Optimierung** | Compiler-Framework (z. B. DSPy) | Ersetzt handgeschriebene Prompts durch messbare, programmierte Optimierungsschleifen. |

---

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | [LangChain](https://github.com/langchain-ai/langchain) | MIT | Hoch | Dokumentiertes Ökosystem für Modellketten, Agenten, Prompts und Tool-Calling. | PostgreSQL: [Dokumente und Vektoren über langchain-postgres](https://github.com/langchain-ai/langchain-postgres) |
| 2 | [LlamaIndex](https://github.com/run-llama/llama_index) | MIT | Hoch | Bibliothek für Dokumentabruf und Modellanbindung. | PostgreSQL: [PGVectorStore-Integration](https://developers.llamaindex.ai/python/framework-api-reference/storage/vector_store/postgres/) |
| 3 | [Ollama](https://github.com/ollama/ollama) | MIT | Hoch | Laufzeit für lokale Modelle; Modelllizenz und Konfiguration separat prüfen. | Dateien: [Lokale Modell- und GGUF-Dateien](https://ollama.com/) |
| 4 | [LiteLLM](https://github.com/BerriAI/litellm) | MIT | Hoch | Universelles OpenAI-kompatibles Gateway für über 100 Modellanbieter mit Load-Balancing. | PostgreSQL: [PostgreSQL für Proxy-Schlüssel und Budgets](https://docs.litellm.ai/docs/proxy/virtual_keys) |
| 5 | [DSPy](https://github.com/stanfordnlp/dspy) | MIT | Hoch | Framework von Stanford zur programmatischen Optimierung von Prompts und LLM-Pipelines. | Dateien: [JSON-Konfigurations- und Optimierungsdateien](https://dspy.ai/) |

---

## Einsatz und Abgrenzung

Integrationsbibliotheken lösen Anwendungsentwickler von herstellerspezifischen API-Besonderheiten, unterscheiden sich jedoch grundlegend in ihrem architektonischen Schwerpunkt:

- **LangChain:** Eignet sich als modulares Werkzeug- und Ketten-Ökosystem, wenn vielseitige Integrationen zu externen Datenquellen und Tool-Calling benötigt werden. Für einfache Aufrufe erzeugen die tiefen Vererbungshierarchien jedoch unnötige Komplexität.
- **LlamaIndex:** Konzentriert sich primär auf die Datenaufnahme, Chunking-Strategien und multimodales Retrieval. Es dient als Kernbaustein für RAG-Systeme, delegiert weiterführende Anwendungslogik jedoch an das übergeordnete Backend.
- **Ollama:** Bietet eine isolierte Laufzeitumgebung zur Ausführung quantisierter Open-Weights-Modelle auf eigener Hardware. Es ersetzt weder eine Vektordatenbank noch die semantische Anwendungslogik, sondern dient als lokaler API-Endpunkt.
- **LiteLLM:** Wirkt als standardisierende Schicht zwischen Anwendungscode und diversen Cloud- oder On-Premise-Modellanbietern. Der Betrieb eines separaten Proxy-Dienstes erfordert zusätzliche Infrastruktur, schützt jedoch vor Anbieter-Lock-in und unkontrollierten API-Kosten.
- **DSPy:** Verfolgt einen algorithmischen Ansatz, der Prompts wie kompilierbare Programme behandelt. Es optimiert Few-Shot-Beispiele und Instruktionen anhand messbarer Evaluationsmetriken, setzt dafür aber einen gepflegten Satz an Testdaten voraus.

Zur praktischen Anbindung auf Backend-Ebene siehe [Sprachmodelle in Webframeworks & Backend](frameworks.md). Für autonome Entwicklungsassistenten, die Projektdateien bearbeiten, sei auf [KI-native Bausteine und agentengestützte Entwicklung](../webframeworks/ki-agenten.md) sowie [KI- und CLI-Coding-Agenten im Vergleich](../cli-agenten.md) verwiesen.
