# Agentische Content-Systeme

[Übergeordnete Kategorie: Evolution digitaler Content-Management-Systeme](../cms.md)

Bausteine für mehrstufige Recherche-, Schreib- und Prüfabläufe.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
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

CMS-Anbindung und Publikationsfreigabe sind selbst zu gestalten. Hohe Framework-Reife belegt keine fehlerfreie autonome Veröffentlichung.

- **LangGraph:** Werkzeuge, Modelle und Freigaben selbst konfigurieren.
- **Haystack:** Anwendung, Index und Evaluation müssen integriert werden.
- **LlamaIndex:** Gehostete Angebote sind von der offenen Bibliothek zu trennen.
- **Microsoft Agent Framework:** Junger Nachfolger; langfristige Betriebserfahrung noch begrenzt.

Projektentwicklung: [Semantic Kernel verweist auf Microsoft Agent Framework als Nachfolger](https://github.com/microsoft/semantic-kernel). Die Bewertung bleibt wegen der jungen Projektlinie vorsichtig.

- **LangChain:** Framework mit dokumentierten [Multi-Agenten-Mustern](https://docs.langchain.com/oss/python/langchain/multi-agent). Es ergänzt die Orchestrierung um Modell- und Werkzeuganbindungen. PostgreSQL für Dokumente und Vektoren sowie PostgreSQL-basierte Zustandsverwaltung konfigurieren; keine fertige CMS-Oberfläche.
