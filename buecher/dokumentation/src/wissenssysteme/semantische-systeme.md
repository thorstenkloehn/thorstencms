# Semantische und RAG-Systeme

[Übergeordnete Kategorie: Digitale Wissenssysteme](../wissenssysteme.md)

Bedeutungsorientiertes Erschließen von Dokumenten und Wissen.

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

Ein semantisches Wissenssystem erschließt Inhalte über Bedeutungsähnlichkeiten, Entitäten und Wissensgraphen. Es ergänzt strukturierte Wikis, ersetzt jedoch weder redaktionelle Pflege noch Zugriffsrechte.

- **Haystack:** Ermöglicht hybride Sucharchitekturen aus traditioneller Volltextsuche (BM25) und dichter Vektorsuche für komplexe Wissensbestände.
- **LlamaIndex:** Bietet Datenstrukturen zur Extraktion und Traversierung hierarchischer Wissensgraphen aus verknüpften Notizen und Dokumenten.
- **LangChain:** Verbindet Wissensspeicher mit Abfrageketten; die semantische Konsistenz erfordert anwendungsspezifische Filterregeln.
- **AnythingLLM:** Bietet getrennte Arbeitsbereiche (Workspaces) für unterschiedliche Wissensthemen. Zur Einhaltung des Speicherfilters ist die [Umstellung auf PostgreSQL und pgvector](../software.md#sonderfall-anythingllm) erforderlich.
- **LangGraph:** Modelliert mehrschrittige Recherchepfade und Begriffsklärungen als zustandsbehaftete Graphen mit expliziten Verzweigungsregeln.
