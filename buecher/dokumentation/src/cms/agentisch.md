# Agentische Content-Systeme

[Übergeordnete Kategorie: Content-Management-Systeme](../cms.md)

Bausteine für mehrstufige Recherche-, Schreib- und Prüfabläufe.

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

Agentische Systeme im CMS automatisieren mehrstufige redaktionelle Aufgaben wie Recherche, Erstentwurf und Faktenabgleich. Die redaktionelle Freigabe und Qualitätskontrolle müssen als feste Kontrollpunkte (Human-in-the-Loop) verankert bleiben.

- **LangGraph:** Bildet redaktionelle Genehmigungsketten (z. B. Recherche -> Entwurf -> Faktenprüfung -> finale Freigabe) als zustandsbehafteten Graphen ab.
- **Haystack:** Dient als spezialisierter Prüfbaustein, um Aussagen in Textentwürfen automatisiert gegen freigegebene Unternehmensquellen abzugleichen.
- **LlamaIndex:** Versorgt Schreib-Agenten mit thematisch passenden Referenzdokumenten und Metadaten aus dem Inhaltsarchiv des CMS.
- **Microsoft Agent Framework:** Ermöglicht die Orchestrierung asynchroner Redaktionsaufgaben; als Nachfolger des Semantic Kernel verlangt die junge Codebasis noch vorsichtige Erprobung.
- **LangChain:** Stellt [Multi-Agenten-Muster](https://docs.langchain.com/oss/python/langchain/multi-agent) und Werkzeug-Adapter für CMS-APIs bereit; alle Zwischenzustände und Token-Budgets sind in PostgreSQL zu sichern.
