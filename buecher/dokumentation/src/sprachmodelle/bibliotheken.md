# KI-Integrations- und Modellbibliotheken

[Übergeordnete Kategorie: Integration von Sprachmodellen in Software-Architekturen](../sprachmodell-integration.md)

Abstraktionsbibliotheken, Prompt-Orchestrierung, Gateways und lokale Open-Weights-Laufzeiten.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [LangChain](https://github.com/langchain-ai/langchain) | MIT | Sehr hoch | Umfassendes Ökosystem für Modellketten, Agenten, Prompts und Tool-Calling. | PostgreSQL: [PostgreSQL-Checkpointer und langchain-postgres](https://github.com/langchain-ai/langchain-postgres) |
| 2 | [LlamaIndex](https://github.com/run-llama/llama_index) | MIT | Sehr hoch | Führendes Daten-Framework zur Verbindung privater Dokumente mit Sprachmodellen. | PostgreSQL: [PGVectorStore-Integration](https://docs.llamaindex.ai/) |
| 3 | [Ollama](https://github.com/ollama/ollama) | MIT | Sehr hoch | Standard für den lokalen, datenschutzkonformen Betrieb von Open-Weights-Modellen. | Dateien: [Lokale Modell- und GGUF-Dateien](https://ollama.com/) |
| 4 | [LiteLLM](https://github.com/BerriAI/litellm) | MIT | Sehr hoch | Universelles OpenAI-kompatibles Gateway für über 100 Modellanbieter mit Load-Balancing. | PostgreSQL: [PostgreSQL-Proxy-Datenbank für Logging und Budgets](https://docs.litellm.ai/) |
| 5 | [DSPy](https://github.com/stanfordnlp/dspy) | MIT | Hoch | Framework von Stanford zur programmatischen Optimierung von Prompts und LLM-Pipelines. | Dateien: [JSON-Konfigurations- und Optimierungsdateien](https://dspy.ai/) |

## Einsatz und Abgrenzung

Integrationsbibliotheken lösen Anwendungsentwickler von herstellerspezifischen API-Besonderheiten.

- **LangChain:** Extrem breite Werkzeug- und Vektorunterstützung; Abstraktionen können bei einfachen Aufrufen komplex wirken.
- **LlamaIndex:** Spezialisiert auf Indizierung, Chunking und Retrieval; optimal für wissensintensive Workflows.
- **Ollama:** Ermöglicht vollständige Datenhoheit ohne Cloud-Kosten; setzt ausreichende lokale GPU-/RAM-Ressourcen voraus.
- **LiteLLM:** Zentralisiert Authentifizierung, Kostenkontrolle und Fallbacks; erfordert Betrieb eines Proxy-Dienstes.
- **DSPy:** Ersetzt manuelles Prompt-Engineering durch Compiler-Optimierung; erfordert Trainingsbeispiele und Evaluationsmetriken.
