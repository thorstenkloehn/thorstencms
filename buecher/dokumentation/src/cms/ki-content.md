# KI-gestützte Content-Erstellung

[Übergeordnete Kategorie: Evolution digitaler Content-Management-Systeme](../cms.md)

Offene Erweiterungen und Frameworks für Assistenz in Redaktionsprozessen.

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
| 4 | [Drupal AI](https://www.drupal.org/project/ai) | GPL-2.0-or-later | Mittel | Offizielle Drupal-Projektseite mit Releases und Dokumentation. | PostgreSQL: [PostgreSQL über Drupal; externe KI-Speicher separat konfigurieren](https://www.drupal.org/docs/getting-started/system-requirements/database-server-requirements) |
| 5 | [Microsoft Agent Framework](https://github.com/microsoft/agent-framework) | MIT | Mittel | Dokumentierte Workflows, Beispiele und Supportinformationen. | Dateien: [Datei-Checkpoints via FileCheckpointStorage](https://learn.microsoft.com/en-us/agent-framework/workflows/checkpoints) |

## Einsatz und Abgrenzung

Drupal AI ist eine CMS-Erweiterung. Die anderen Einträge sind Integrationsbausteine für Textassistenz oder dokumentengestützte Verarbeitung; eine fertige Personalisierungsplattform wird damit nicht zugesichert.

- **Haystack:** Anwendung, Index und Evaluation müssen integriert werden.
- **LlamaIndex:** Gehostete Angebote sind von der offenen Bibliothek zu trennen.
- **LangChain:** Framework liefert keine fertige Wissensredaktion.
- **Drupal AI:** Reife des Drupal-Kerns überträgt sich nicht automatisch auf KI-Module.
- **Microsoft Agent Framework:** Junger Nachfolger; langfristige Betriebserfahrung noch begrenzt.

Projektentwicklung: [Semantic Kernel verweist auf Microsoft Agent Framework als Nachfolger](https://github.com/microsoft/semantic-kernel). Die Bewertung bleibt wegen der jungen Projektlinie vorsichtig.
