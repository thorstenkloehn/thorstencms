# RAG- und KI-Wissenssysteme

[Übergeordnete Kategorie: Dokumentenerstellung, Wikis und Notebooks](../dokumentation.md)

Dokumentengestützte Suche und Antworten aus einem eigenen Wissensbestand.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Haystack](https://github.com/deepset-ai/haystack) | Apache-2.0 (Kern) | Hoch | Dokumentierte Pipelines, Tests und Migrationshinweise. | PostgreSQL: [PostgreSQL + pgvector für Dokumente und Vektoren](https://docs.haystack.deepset.ai/reference/integrations-pgvector) |
| 2 | [LlamaIndex](https://github.com/run-llama/llama_index) | MIT (Kern) | Hoch | Dokumentation, Beispiele und nachvollziehbarer Änderungsverlauf. | Dateien: [Lokale Dateien via StorageContext.persist](https://developers.llamaindex.ai/python/framework/module_guides/storing/save_load/) |
| 3 | [LangChain](https://github.com/langchain-ai/langchain) | MIT (Bibliothek) | Hoch | Dokumentierte Integrationen und Sicherheitsrichtlinie. | PostgreSQL: [PostgreSQL über langchain-postgres](https://github.com/langchain-ai/langchain-postgres) |
| 4 | [LangGraph](https://github.com/langchain-ai/langgraph) | MIT (Bibliothek) | Hoch | Dokumentierte Abläufe mit Zustandsverwaltung. | PostgreSQL: [PostgreSQL-Checkpointer und Store konfigurieren](https://docs.langchain.com/oss/python/langgraph/persistence) |
| 5 | [AnythingLLM](https://github.com/Mintplex-Labs/anything-llm) | MIT (Kern) | Mittel für PostgreSQL-Betrieb | PostgreSQL-Pfad im Quellprojekt beschrieben; zusätzliche Einrichtung erforderlich. | PostgreSQL: [Prisma-Datenbank umstellen](https://github.com/Mintplex-Labs/anything-llm/blob/master/server/prisma/schema.prisma) und [pgvector konfigurieren](https://github.com/Mintplex-Labs/anything-llm/blob/master/server/utils/vectorDbProviders/pgvector/SETUP.md) |

## Einsatz und Abgrenzung

RAG-Systeme ergänzen Dokumentensammlungen um semantische Suche und kontextbezogene Antworten, garantieren jedoch keine fehlerfreie Wiedergabe. Die Frameworks Haystack, LlamaIndex, LangChain und LangGraph erfordern eine eigene Anwendungs- und Indexierungslogik.

- **Haystack:** Spezialisiert auf modulare Frage-Antwort-Pipelines, Dokument-Routing und systematische Evaluierung von Antworttreffern.
- **LlamaIndex:** Schwerpunkt liegt auf Chunking-Strategien, Knoten-Hierarchien und optimiertem Dokumenten-Retrieval aus Dateien.
- **LangChain:** Breit gefächerte Schnittstellenbibliothek für Prompt-Verkettungen und PostgreSQL-Vektorspeicher; erfordert eigene Oberfläche.
- **AnythingLLM:** Sofort nutzbare Chat-Oberfläche für Dokumentensammlungen; setzt für den filterkonformen Betrieb die [Umstellung auf PostgreSQL und pgvector](../software.md#sonderfall-anythingllm) voraus.
- **LangGraph:** Ermöglicht zyklische [Agentic-RAG-Abläufe](https://docs.langchain.com/oss/python/langgraph/agentic-rag) mit adaptiver Re-Querying- und Selbstkorrekturlogik bei unvollständigen Suchergebnissen.
