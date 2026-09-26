# Agentische Dokumentationspflege

[Übergeordnete Kategorie: Docs-as-Code](../docs-as-code.md)

Offene Assistenten und Agenten für Änderungen an Dokumentations-Repositories.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Aider](https://github.com/Aider-AI/aider) | Apache-2.0 | Hoch | Dokumentierter Terminal-Workflow mit Modellanbindung. | Dateien: [Repository-Dateien und textuelle Chat-Historie](https://aider.chat/docs/config/options.html) |
| 2 | [Cline](https://github.com/cline/cline) | Apache-2.0 | Hoch | Dokumentierter Assistent für Änderungen und Prüfung von Repository-Dateien. | Dateien: [Repository-Inhalte und persistierte Nachrichten als JSON](https://docs.cline.bot/sdk/clinecore) |
| 3 | [LangGraph](https://github.com/langchain-ai/langgraph) | MIT (Bibliothek) | Hoch | Dokumentierte Abläufe mit Zustandsverwaltung. | PostgreSQL: [PostgreSQL-Checkpointer und Store konfigurieren](https://docs.langchain.com/oss/python/langgraph/persistence) |
| 4 | [mini-SWE-agent](https://github.com/SWE-agent/mini-swe-agent) | MIT | Mittel | Dokumentierte Migration und schlanke Agentenarchitektur. | Dateien: [Repository-Dateien und JSON-Trajektorien](https://mini-swe-agent.com/v2/usage/mini/) |
| 5 | [Gemini CLI](https://github.com/google-gemini/gemini-cli) | Apache-2.0 | Mittel | Dokumentierter Terminal-Agent; kürzere Langzeiterfahrung als etablierte Dokumentationswerkzeuge. | Dateien: [Repository-Inhalte und lokale Sitzungsdateien](https://geminicli.com/docs/cli/session-management/) |

## Einsatz und Abgrenzung

Aider bearbeitet Repository-Dateien und führt eine textuelle Historie. mini-SWE-agent speichert Abläufe als JSON-Dateien. Inhaltliche Prüfung und Buch-Build bleiben Teil des Arbeitsprozesses.

- **Aider:** Assistiertes Bearbeiten ist keine garantierte autonome Pflege.
- **mini-SWE-agent:** Benchmark-Ergebnisse ersetzen keine Dokumentationsprüfung.

- **Cline:** Assistent für Repository-Dateien mit lokaler Nachrichtenpersistenz. Dokumentationsänderungen benötigen weiterhin fachliches Review und einen erfolgreichen Build.

- **Gemini CLI:** Der offene CLI-Kern bearbeitet lokale Dateien und speichert Sitzungen lokal. Die Lizenz eines angebundenen Modells oder Dienstes ist davon unabhängig.

- **LangGraph:** Ermöglicht die Entwicklung maßgeschneiderter Dokumentationsagenten mit zustandsbehafteten Korrekturschleifen (z. B. automatisierte Syntax- oder Linkprüfung mit iterativem Nachbessern vor dem Commit). PostgreSQL-Checkpointer sichern den Agentenzustand zwischen einzelnen Arbeitsschritten.
