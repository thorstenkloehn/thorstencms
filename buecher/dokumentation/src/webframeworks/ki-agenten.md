# KI-native Bausteine und agentengestützte Entwicklung

[Übergeordnete Kategorie: Webframeworks](../webframeworks.md)

Die Quelle behandelt sowohl KI-Funktionen in Webanwendungen als auch externe Entwicklungsassistenten. Die folgende Auswahl unterscheidet deshalb Laufzeit-Orchestrierung und Werkzeuge zur Bearbeitung eines Webprojekts.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien in der beschriebenen Betriebsvariante.

Stand: **26. September 2026**. [Bewertungskriterien und Grenzen](../software.md).

| Rang | Software und offizielle Quelle | Lizenz des Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [LangGraph](https://github.com/langchain-ai/langgraph) | MIT (Bibliothek) | Hoch | Dokumentierte Abläufe mit Zustandsverwaltung. | PostgreSQL: [PostgreSQL-Checkpointer und Store konfigurieren](https://docs.langchain.com/oss/python/langgraph/persistence) |
| 2 | [Aider](https://github.com/Aider-AI/aider) | Apache-2.0 | Hoch | Dokumentierter Terminal-Workflow mit Modellanbindung. | Dateien: [Repository-Dateien und textuelle Chat-Historie](https://aider.chat/docs/config/options.html) |
| 3 | [Cline](https://github.com/cline/cline) | Apache-2.0 | Hoch | Dokumentierter Assistent für Änderungen und Prüfung von Repository-Dateien. | Dateien: [Repository-Inhalte und persistierte Nachrichten als JSON](https://docs.cline.bot/sdk/clinecore) |
| 4 | [mini-SWE-agent](https://github.com/SWE-agent/mini-swe-agent) | MIT | Mittel | Dokumentierte Migration und schlanke Agentenarchitektur. | Dateien: [Repository-Dateien und JSON-Trajektorien](https://mini-swe-agent.com/v2/usage/mini/) |
| 5 | [Gemini CLI](https://github.com/google-gemini/gemini-cli) | Apache-2.0 | Mittel | Dokumentierter Terminal-Agent; kürzere Langzeiterfahrung als etablierte Dokumentationswerkzeuge. | Dateien: [Repository-Inhalte und lokale Sitzungsdateien](https://geminicli.com/docs/cli/session-management/) |

## Einsatz und Abgrenzung

LangGraph ist ein Framework für KI-Abläufe und benötigt eine Web-API und Oberfläche. Die übrigen vier Projekte sind Entwicklungsassistenten, keine Webframeworks: Sie bearbeiten lokale Projektdateien. Ihre Dateispeicherung sagt nichts über die Datenbank der erzeugten Webanwendung aus; diese muss zusätzlich den Filter erfüllen. Die Reifegrade bewerten die Werkzeuge, nicht automatisch erzeugte Anwendungen.

Thematische Grundlage: [Evolution digitaler Webframeworks](https://dokument.wissen-ahrensburg.de/entwicklung/webentwicklung/evolution-digitaler-webframeworks/).
