# RAG- und KI-Wissenssysteme

[Übergeordnete Kategorie: Dokumentenerstellung, Wikis und Notebooks](../dokumentation.md)

Dokumentengestützte Suche und Antworten aus einem eigenen Wissensbestand.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
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

Die ersten drei Einträge sind Frameworks; AnythingLLM ergänzt eine Anwendung mit gesondert einzurichtendem PostgreSQL-Betrieb. Haystack und LangChain sind mit PostgreSQL-Integrationen nutzbar; LlamaIndex kann seine einfachen Speicherstrukturen lokal persistieren. Die jeweils genannte Speicheroption muss ausdrücklich gewählt werden.

- **Haystack:** Anwendung, Index und Evaluation müssen integriert werden.
- **LlamaIndex:** Gehostete Angebote sind von der offenen Bibliothek zu trennen.
- **LangChain:** Framework liefert keine fertige Wissensredaktion.

- **AnythingLLM:** Nur der PostgreSQL-Betrieb bleibt ausgewählt: Prisma-Datenbank gemäß Quellhinweis umstellen und pgvector als Vektorspeicher einrichten. Die Standardinstallation mit SQLite erfüllt den Filter nicht. Dieser zusätzliche Anpassungsbedarf begrenzt die Reife dieser Betriebsvariante.

- **LangGraph:** Framework für selbst entwickelte Abläufe, keine fertige Redaktionsanwendung. [RAG-Abläufe](https://docs.langchain.com/oss/python/langgraph/agentic-rag) lassen sich damit orchestrieren. PostgreSQL-Checkpointer und Store ausdrücklich konfigurieren; für Dokumente und Vektoren bei Bedarf [langchain-postgres](https://github.com/langchain-ai/langchain-postgres) einsetzen. Für Dokumentationspflege müssen Dateibearbeitung, Review und Build als Werkzeuge eingebunden werden.
