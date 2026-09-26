# KI-Unterstützung und dokumentengestützte Suche

[Übergeordnete Kategorie: Docs-as-Code](../docs-as-code.md)

Offene Software für RAG-Suche und die Integration von Dokumentationsassistenz.

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

Diese Auswahl fokussiert auf KI-Unterstützung im Dokumentationsprozess. Sprachmodelle und RAG-Pipelines können Dokumentbestände durchsuchen oder Konsistenz prüfen, ersetzen aber weder automatisierte Linters noch deterministische Build-Läufe.

- **Haystack:** Ermöglicht semantische Suche über versionierten Markdown- und Textbeständen; Indexierung und Auswertung müssen in die Dokumentations-Pipeline integriert werden.
- **LlamaIndex:** Unterstützt das Einlesen und Strukturieren dateibasierter Dokumentenquellen; die offene Bibliothek ist von gehosteten Zusatzangeboten zu trennen.
- **LangChain:** Liefert Integrationsketten für Dokumentenabfragen; für eine automatisierte Redaktionsprüfung müssen konkrete Regeln und Werkzeuge selbst definiert werden.
- **AnythingLLM:** Bietet eine Desktop- und Web-Schnittstelle zur Abfrage von Textbeständen. Zur Einhaltung des Speicherfilters ist die Konfiguration von [PostgreSQL und pgvector](../software.md#sonderfall-anythingllm) zwingend erforderlich.
- **LangGraph:** Eignet sich zur Steuerung mehrstufiger Prüf- und Korrekturabläufe bei Pull Requests. PostgreSQL-Checkpointer sind explizit einzurichten; Dateibearbeitung und Linter werden als Werkzeuge angebunden.
