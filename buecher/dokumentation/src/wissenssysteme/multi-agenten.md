# Multimodale Multi-Agenten-Systeme

[Übergeordnete Kategorie: Digitale Wissenssysteme](../wissenssysteme.md)

Offene Bausteine zur Orchestrierung spezialisierter Wissensagenten.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [LangGraph](https://github.com/langchain-ai/langgraph) | MIT (Bibliothek) | Hoch | Dokumentierte Abläufe mit Zustandsverwaltung. | PostgreSQL: [PostgreSQL-Checkpointer und Store konfigurieren](https://docs.langchain.com/oss/python/langgraph/persistence) |
| 2 | [Haystack](https://github.com/deepset-ai/haystack) | Apache-2.0 (Kern) | Hoch | Dokumentierte Pipelines, Tests und Migrationshinweise. | PostgreSQL: [PostgreSQL + pgvector für Dokumente und Vektoren](https://docs.haystack.deepset.ai/reference/integrations-pgvector) |
| 3 | [LlamaIndex](https://github.com/run-llama/llama_index) | MIT (Kern) | Hoch | Dokumentation, Beispiele und nachvollziehbarer Änderungsverlauf. | Dateien: [Lokale Dateien via StorageContext.persist](https://developers.llamaindex.ai/python/framework/module_guides/storing/save_load/) |
| 4 | [LangChain](https://github.com/langchain-ai/langchain) | MIT (Bibliothek) | Hoch | Dokumentierte Integrationen und Sicherheitsrichtlinie. | PostgreSQL: [PostgreSQL über langchain-postgres](https://github.com/langchain-ai/langchain-postgres) |
| 5 | [Microsoft Agent Framework](https://github.com/microsoft/agent-framework) | MIT | Mittel | Dokumentierte Workflows, Beispiele und Supportinformationen. | Dateien: [Datei-Checkpoints via FileCheckpointStorage](https://learn.microsoft.com/en-us/agent-framework/workflows/checkpoints) |

## Einsatz und Abgrenzung

Multi-Agenten-Systeme verteilen komplexe Recherche- und Analyseaufgaben auf spezialisierte Agenten, die Zwischenergebnisse austauschen und gegenseitig validieren.

- **LangGraph:** Ermöglicht zyklische Agenten-Netzwerke mit expliziter Rollenverteilung (z. B. Recherche, Synthese und kritischer Gegenabgleich) über persistente PostgreSQL-Checkpoints.
- **Haystack:** Integriert multimodale Datenquellen (Text, Tabellen, strukturierte Daten) in vernetzte Agenten-Pipelines mit formalen Bewertungsmetriken.
- **LlamaIndex:** Fungiert als strukturierte Wissensebene für autonome Agenten, die semantische Indizes und Dokumentenhierarchien navigieren.
- **Microsoft Agent Framework:** Bietet ein verteiltes Laufzeitmodell für Unternehmens-Agenten mit starker Typisierung; die noch junge Plattform erfordert gezielte Schnittstellenpflege.
- **LangChain:** Dokumentierte [Multi-Agenten-Muster](https://docs.langchain.com/oss/python/langchain/multi-agent) zur Orchestrierung von Experten-Agenten; Agentenzustände und Konversationsverläufe werden in PostgreSQL gespeichert.
