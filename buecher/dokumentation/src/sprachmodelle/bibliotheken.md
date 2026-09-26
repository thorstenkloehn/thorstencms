# KI-Integrations- und Modellbibliotheken

[Übergeordnete Kategorie: Integration von Sprachmodellen in Software-Architekturen](../sprachmodell-integration.md)

Abstraktionsbibliotheken, Prompt-Orchestrierung, Gateways und lokale Open-Weights-Laufzeiten.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [LangChain](https://github.com/langchain-ai/langchain) | MIT | Hoch | Dokumentiertes Ökosystem für Modellketten, Agenten, Prompts und Tool-Calling. | PostgreSQL: [Dokumente und Vektoren über langchain-postgres](https://github.com/langchain-ai/langchain-postgres) |
| 2 | [LlamaIndex](https://github.com/run-llama/llama_index) | MIT | Hoch | Bibliothek für Dokumentabruf und Modellanbindung. | PostgreSQL: [PGVectorStore-Integration](https://developers.llamaindex.ai/python/framework-api-reference/storage/vector_store/postgres/) |
| 3 | [Ollama](https://github.com/ollama/ollama) | MIT | Hoch | Laufzeit für lokale Modelle; Modelllizenz und Konfiguration separat prüfen. | Dateien: [Lokale Modell- und GGUF-Dateien](https://ollama.com/) |
| 4 | [LiteLLM](https://github.com/BerriAI/litellm) | MIT | Hoch | Universelles OpenAI-kompatibles Gateway für über 100 Modellanbieter mit Load-Balancing. | PostgreSQL: [PostgreSQL für Proxy-Schlüssel und Budgets](https://docs.litellm.ai/docs/proxy/virtual_keys) |
| 5 | [DSPy](https://github.com/stanfordnlp/dspy) | MIT | Hoch | Framework von Stanford zur programmatischen Optimierung von Prompts und LLM-Pipelines. | Dateien: [JSON-Konfigurations- und Optimierungsdateien](https://dspy.ai/) |

## Einsatz und Abgrenzung

Integrationsbibliotheken lösen Anwendungsentwickler von herstellerspezifischen API-Besonderheiten.

- **LangChain:** Unterschiedliche Werkzeug- und Vektoranbindungen; Abstraktionen können bei einfachen Aufrufen komplex wirken.
- **LlamaIndex:** Spezialisiert auf Indizierung, Chunking und Retrieval; optimal für wissensintensive Workflows.
- **Ollama:** Lokale und Cloud-Funktionen unterscheiden; Hardwarebedarf hängt vom Modell ab.
- **LiteLLM:** Zentralisiert Authentifizierung, Kostenkontrolle und Fallbacks; erfordert Betrieb eines Proxy-Dienstes.
- **DSPy:** Ersetzt manuelles Prompt-Engineering durch Compiler-Optimierung; erfordert Trainingsbeispiele und Evaluationsmetriken.
