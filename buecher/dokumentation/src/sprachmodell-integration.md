# Integration von Sprachmodellen in Software-Architekturen

Dieses Kapitel betrachtet Sprachmodelle (Large Language Models, LLMs und Small Language Models, SLMs)
nicht als isolierte Chatbot-Schnittstellen, sondern als tief integrierte Architekturbausteine.
Es verbindet die tragenden Säulen dieses Buches – **Content-Management-Systeme (CMS)**,
**Webframeworks**, **KI- und Modellbibliotheken**, **Lernmanagement-Systeme (LMS)**,
**Docs-as-Code**, **Wissenssysteme** sowie **IDEs, Code-Editoren und Office-/Autorentools** – und beschreibt,
wie Sprachmodelle technisch sauber, nachvollziehbar und mit definierter Persistenz angebunden werden.

## Übersicht der Integrationsmuster

Die Anforderungen an Latenz, Interaktionsform, Speicherweg und Fehlertoleranz unterscheiden
sich je nach Systemschicht erheblich:

| Dimension | CMS | Webframeworks & APIs | KI-Bibliotheken | Lernmanagement (LMS) | Wissenssysteme & RAG |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Hauptaufgabe** | Redaktionelle Assistenz & Freigaben | Anwendungslogik & Streaming | Abstraktion, Chains & Gateways | Didaktische Tutoren & Feedback | Vernetzung & Quellensuche |
| **Integrationsort** | Editor-Plugins & CMS-Hooks | Controller, Services & APIs | Anwendungs-Code & Proxys | LTI 1.3 & Kurs-Plugins | RAG-Pipelines & Vektorsuche |
| **Interaktionsmodus** | Interaktiv (Assistent) / Batch | Echtzeit-Streaming (SSE) | Programmatisch (Async/Sync) | Dialog & formative Bewertung | Frage-Antwort mit Zitaten |
| **Speicherweg** | PostgreSQL oder Markdown/YAML | PostgreSQL / pgvector | PostgreSQL oder Modelldateien | PostgreSQL | PostgreSQL (pgvector) oder Dateien |
| **Kritischer Faktor** | Redaktionelle Freigabe | Latenz & State-Handling | Provider-Unabhängigkeit | Didaktische Korrektheit & Ethik | Halluzinationen & Aktualität |

---

## Unterkategorien: gefilterte Softwareauswahl

- [Sprachmodelle in Content-Management-Systemen](sprachmodelle/cms.md)
- [Sprachmodelle in Webframeworks & Backend](sprachmodelle/frameworks.md)
- [KI-Integrations- und Modellbibliotheken](sprachmodelle/bibliotheken.md)
- [Sprachmodelle in Lernmanagement-Systemen](sprachmodelle/lms.md)
- [Sprachmodelle in Docs-as-Code](sprachmodelle/docs-as-code.md)
- [Sprachmodelle in Wissenssystemen](sprachmodelle/wissenssysteme.md)
- [Sprachmodelle in IDEs und Code-Editoren](sprachmodelle/ide-code-editoren.md)
- [Sprachmodelle in Office- und Autorentools](sprachmodelle/office-autorentools.md)

---

## 1. Content-Management-Systeme: Die Redaktionsebene

Im CMS unterstützen Sprachmodelle den redaktionellen Prozess von der Texterfassung bis zur Publikation.

- **In-Editor-Assistenz:** Autoren erhalten direkt im Editor Vorschläge für Textvarianten, Zusammenfassungen,
  SEO-Metadaten oder barrierefreie Alt-Texte für Bildmedien.
- **Event-gesteuerte Hooks:** Beim Speichern oder vor der Publikation triggert das CMS serverseitige Webhooks,
  die automatische Verschlagwortung (Tagging), Taxonomie-Zuweisung oder Übersetzungen anstoßen.
- **Headless- & Composable-Pipelines:** Über standardisierte REST- oder GraphQL-APIs können externe Agenten
  strukturierte Inhalte generieren, validieren und zur Abnahme in die CMS-Datenbank einspielen.
- **Human-in-the-Loop & Governance:** Automatisch generierte Inhalte erfordern eine verbindliche redaktionelle
  Freigabe. Änderungen müssen im Audit-Log versioniert und als KI-unterstützt gekennzeichnet werden (siehe [KI in CMS](sprachmodelle/cms.md)).

---

## 2. Webframeworks: Die interaktive Anwendungsebene

In modernen Webframeworks bilden Sprachmodelle funktionale Bausteine innerhalb der
bestehenden Schichtenarchitektur (MVC / Service-Layer).

- **Framework-native SDKs:** Statt roher HTTP-Aufrufe binden Bibliotheken wie
  *Spring AI* (Java/Spring Boot), *LangChain / DSPy* (Python/Django) oder *Semantic Kernel* (.NET/ASP.NET Core)
  Modellanbieter über austauschbare Abstraktionen an.
- **Echtzeit-Streaming:** Da Sprachmodelle Antworten sequenziell erzeugen, minimieren
  *Server-Sent Events (SSE)* oder WebSockets die gefühlte Wartezeit (Time to First Token) für Benutzer.
- **Tool- & Function-Calling:** Modelle erhalten über JSON-Schemas Zugriff auf interne Backend-Funktionen.
  Sie können so strukturierte Datenbankabfragen über das ORM ausführen oder Schnittstellen aufrufen.
- **Persistenz & Session-Management:** Konversationen, Benutzerprofile und Vektoreinbettungen
  werden in **PostgreSQL** (unter Nutzung der Erweiterung `pgvector`) persistent gehalten (siehe [Webframeworks & Backend](sprachmodelle/frameworks.md)).

---

## 3. KI- und Modellbibliotheken: Abstraktion und Orchestrierung

Entwicklungsbibliotheken bilden das Fundament für die flexible Einbindung und Entkopplung von KI-Diensten.

- **Modell-Gateways:** Werkzeuge wie *LiteLLM* fungieren als OpenAI-kompatible Proxys vor Dutzenden von Modellanbietern. Sie regeln Load-Balancing, Fallbacks und Budget-Limits.
- **Prompt- und Agenten-Orchestrierung:** Frameworks wie *LangChain* und *LlamaIndex* strukturieren mehrstufige Abläufe, Tool-Chains und dynamischen Datenabruf.
- **Lokale Open-Weights-Laufzeiten:** Werkzeuge wie *Ollama* ermöglichen den Betrieb offener Sprachmodelle direkt auf lokaler Hardware, wodurch sensibles Datenmaterial das eigene Rechenzentrum niemals verlässt (siehe [KI-Bibliotheken](sprachmodelle/bibliotheken.md)).

---

## 4. Lernmanagement-Systeme (LMS): Didaktische Assistenz

In E-Learning-Plattformen übernehmen Sprachmodelle didaktische Hilfsfunktionen für Lernende und Lehrende.

- **Adaptive Tutoren:** Lernbegleiter beantworten Fragen zu Vorlesungsmaterialien im Kontext des jeweiligen Kurses (RAG auf Kursebene).
- **Formatierende Feedback-Schleifen:** Bei Freitextaufgaben oder Programmierübungen erhalten Lernende sofortige Hinweise auf Denkfehler, ohne dass die Musterlösung vorweggenommen wird.
- **Automatische Aufgabengenerierung:** Lehrende können aus Skripten und Texten interaktive H5P-Übungen, Quizfragen und Glossareinträge generieren lassen (siehe [Sprachmodelle in LMS](sprachmodelle/lms.md)).

---

## 5. Docs-as-Code und Wissenssysteme

- **Deterministische Builds in Docs-as-Code:** Ein Dokumentations-Build (wie `mdbook build`) muss jederzeit
  reproduzierbar, offlinefähig und deterministisch sein. Nicht-deterministische Modellaufrufe gehören in vorgelagerte Review- oder Vorbereitungsschritte (siehe [Sprachmodelle in Docs-as-Code](sprachmodelle/docs-as-code.md)).
- **RAG und Vektorsuche in Wissenssystemen:** Durch die Verknüpfung von Volltextsuche (Keyword/BM25) mit semantischer Vektorsuche
  (`pgvector`) und expliziten Wissensgraphen (Wikilinks, Taxonomien) werden Halluzinationen verhindert und Fakten belegbar gemacht (siehe [Sprachmodelle in Wissenssystemen](sprachmodelle/wissenssysteme.md)).

---

## 6. IDEs, Code-Editoren und Autorentools

- **IDEs und Code-Editoren:** Lokale Coding-Assistenten integrieren Sprachmodelle direkt in den Arbeitskontext von Entwicklern (Inline-Autovervollständigung, Refactoring und Terminal-Agenten), ohne Abhängigkeiten zu proprietären Diensten zu erzwingen (siehe [Sprachmodelle in IDEs und Code-Editoren](sprachmodelle/ide-code-editoren.md)).
- **Office- und Autorentools:** Schreib- und Redaktionsumgebungen für Text-, Tabellen- und Bürodokumente ermöglichen Zusammenfassungen, Übersetzungen und Stilprüfungen unter Wahrung des Datenschutzes und strikt datei- oder PostgreSQL-basierter Ablage (siehe [Sprachmodelle in Office- und Autorentools](sprachmodelle/office-autorentools.md)).

---

## 7. Querschnittsanforderungen: Persistenz, Latenz und Guardrails

Beim produktiven Betrieb über alle Säulen hinweg sind drei zentrale Querschnittsfragen zu lösen:

1. **Speicherarchitektur:**
   Ausschließlich **PostgreSQL** (für relationale Daten, Audit-Logs und Vektoren via `pgvector`)
   oder **Dateisysteme** (Markdown, JSON, HTML). Spezialdatenbanken ohne dokumentierte Persistenz widersprechen einer stabilen Betriebsführung (siehe [Verbindlicher Speicherfilter](software.md#verbindlicher-speicherfilter)).
2. **Asynchrone Entkopplung:**
   Sprachmodellaufrufe dauern oft Sekunden. Hintergrundprozesse (Builds, Indizierung, automatische Übersetzungen) müssen über asynchrone Task-Queues vom interaktiven Thread entkoppelt werden.
3. **Strukturierte Ausgaben & Guardrails:**
   Werden Modellausgaben an nachgelagerte Systeme übergeben, müssen sie über strikte JSON-Schemas (z. B. Pydantic) validiert und im Fehlerfall abgefangen werden.

---

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: 26. September 2026. Redaktionelle Auswahl nach der
[gemeinsamen Bewertungsmethode](software.md). Die Reihenfolge priorisiert
Reife und anschließend die Eignung für diese Kategorie.

| Rang | Software | Lizenz des Kerns | Reifegrad | Schwerpunkt | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [LangChain](https://github.com/langchain-ai/langchain) | MIT | Sehr hoch | Umfassende Modell-Orchestrierung und Tool-Chains | PostgreSQL: [PostgreSQL-Checkpointer und Store](https://github.com/langchain-ai/langchain-postgres) |
| 2 | [LlamaIndex](https://github.com/run-llama/llama_index) | MIT | Sehr hoch | Daten-Framework für Dokumenten-Indizierung und RAG | PostgreSQL: [PGVectorStore-Integration](https://docs.llamaindex.ai/) |
| 3 | [Ollama](https://github.com/ollama/ollama) | MIT | Sehr hoch | Lokale Laufzeitumgebung für Open-Weights-Sprachmodelle | Dateien: [Lokale Modell- und GGUF-Dateien](https://ollama.com/) |
| 4 | [LiteLLM](https://github.com/BerriAI/litellm) | MIT | Sehr hoch | Zentrales Gateway und Proxy für 100+ Modellanbieter | PostgreSQL: [PostgreSQL-Proxy-Datenbank für Logs und Budgets](https://docs.litellm.ai/) |
| 5 | [Dify](https://github.com/langgenius/dify) | Apache-2.0 | Hoch | Visuelle Anwendungsplattform für RAG, Agenten und Workflows | PostgreSQL: [PostgreSQL als zentrale relationale Datenbank](https://docs.dify.ai/) |

### 1. LangChain

**Begründung:** Weitverbreitetes Standard-Ökosystem zur Verknüpfung von Sprachmodellen mit externen Datenquellen, relationalen Datenbanken und APIs.

**Einordnung:** Mächtige Abstraktionsschichten erfordern saubere Architekturentscheidungen zur Vermeidung unnötiger Komplexität.

Offizielle Grundlage: [LangChain](https://github.com/langchain-ai/langchain).

### 2. LlamaIndex

**Begründung:** Führendes Daten-Framework für fortgeschrittenes Chunking, Parsing und hierarchisches Retrieval privater Dokumente.

**Einordnung:** Spezialisiert auf wissensbasierte Abfragen und RAG; für allgemeine Multi-Agenten-Workflows oft mit LangGraph kombiniert.

Offizielle Grundlage: [LlamaIndex](https://github.com/run-llama/llama_index).

### 3. Ollama

**Begründung:** Etablierter Open-Source-Standard zur lokalen Ausführung von Open-Weights-Modellen (Llama, Mistral, Qwen) mit nativer OpenAI-API-Kompatibilität.

**Einordnung:** Bietet vollständige Datenkontrolle; setzt leistungsfähige Hardware (GPU/VRAM) auf dem Hostsystem voraus.

Offizielle Grundlage: [Ollama](https://github.com/ollama/ollama).

### 4. LiteLLM

**Begründung:** Universelles Proxy-Gateway, das Aufrufe an über 100 LLM-APIs in einem standardisierten Format zusammenführt und Kostenkontrolle ermöglicht.

**Einordnung:** Gateway- und Routing-Komponente; ersetzt keine fachliche Anwendungslogik.

Offizielle Grundlage: [LiteLLM](https://github.com/BerriAI/litellm).

### 5. Dify

**Begründung:** Vollständige visuelle Entwicklungsplattform für KI-Assistenten und RAG-Pipelines mit integrierter Prompt-Verwaltung und API-Auslieferung.

**Einordnung:** Höherer Betriebsaufwand (Docker/Kubernetes-Stack) als schlanke Programmbibliotheken.

Offizielle Grundlage: [Dify](https://github.com/langgenius/dify).

---

## Verwandte Kapitel

- [KI- und CLI-Coding-Agenten im Vergleich](cli-agenten.md): Detaillierte Betrachtung von Claude Code, AGY CLI und Aider.
- [Mobile und Desktop-Apps in Content- und Wissenssystemen](mobile-desktop-apps.md): App-Architekturen und Offline-Synchronisation.
- [Architekturen im Zusammenhang](architekturen.md): Das Zusammenspiel verschiedener Informationssysteme.
- [Softwareauswahl und Reifegrade](software.md): Kriterien für PostgreSQL- und Dateibetrieb.
