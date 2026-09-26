# Sprachmodelle in Wissenssystemen

[Übergeordnete Kategorie](../sprachmodell-integration.md)

Dokumentengestützte Antworten benötigen einen gepflegten Bestand, geeigneten Abruf und eine Prüfung der erzeugten Aussagen.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**. [Bewertungskriterien und Grenzen](../software.md).

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Haystack](https://github.com/deepset-ai/haystack) | Apache-2.0 (Kern) | Hoch | Dokumentierte Pipelines, Tests und Migrationshinweise. | PostgreSQL: [PostgreSQL + pgvector für Dokumente und Vektoren](https://docs.haystack.deepset.ai/reference/integrations-pgvector) |
| 2 | [LlamaIndex](https://github.com/run-llama/llama_index) | MIT (Kern) | Hoch | Dokumentation, Beispiele und nachvollziehbarer Änderungsverlauf. | Dateien: [Lokale Dateien via StorageContext.persist](https://developers.llamaindex.ai/python/framework/module_guides/storing/save_load/) |
| 3 | [LangChain](https://github.com/langchain-ai/langchain) | MIT (Bibliothek) | Hoch | Dokumentierte Integrationen und Sicherheitsrichtlinie. | PostgreSQL: [PostgreSQL über langchain-postgres](https://github.com/langchain-ai/langchain-postgres) |
| 4 | [LangGraph](https://github.com/langchain-ai/langgraph) | MIT (Bibliothek) | Hoch | Dokumentierte Abläufe mit Zustandsverwaltung. | PostgreSQL: [PostgreSQL-Checkpointer und Store konfigurieren](https://docs.langchain.com/oss/python/langgraph/persistence) |
| 5 | [AnythingLLM](https://github.com/Mintplex-Labs/anything-llm) | MIT (Kern) | Mittel für PostgreSQL-Betrieb | PostgreSQL-Pfad im Quellprojekt beschrieben; zusätzliche Einrichtung erforderlich. | PostgreSQL: [Prisma-Datenbank umstellen](https://github.com/Mintplex-Labs/anything-llm/blob/master/server/prisma/schema.prisma) und [pgvector konfigurieren](https://github.com/Mintplex-Labs/anything-llm/blob/master/server/utils/vectorDbProviders/pgvector/SETUP.md) |

## Einsatz und Abgrenzung

Haystack, LlamaIndex, LangChain und LangGraph sind Bausteine für eigene
Anwendungen. Für eine Wissensredaktion müssen Suche, Berechtigungen,
Quellenverweise und Aktualisierung der Daten zusammengeführt werden.

AnythingLLM bleibt ausschließlich als angepasste PostgreSQL-Variante enthalten:
Anwendungsdatenbank gemäß [Prisma-Schema](https://github.com/Mintplex-Labs/anything-llm/blob/master/server/prisma/schema.prisma)
umstellen und [pgvector](https://github.com/Mintplex-Labs/anything-llm/blob/master/server/utils/vectorDbProviders/pgvector/SETUP.md)
einrichten. pgvector allein ersetzt die standardmäßige SQLite-Anwendungsdatenbank
nicht. Diese Umstellung wurde für das Buch nicht praktisch getestet.

Eine erzeugte Antwort wird gegen die verwendeten Passagen geprüft. RAG kann
die Quellenarbeit unterstützen, garantiert aber keine fehlerfreien Aussagen.
Für Wiki.js werden hier keine unbewiesenen nativen Vektor- oder RAG-Funktionen
behauptet; die Wiki-Nutzung bleibt in der entsprechenden Kategorie beschrieben.
