# Sprachmodelle in Docs-as-Code

[Übergeordnete Kategorie: Integration von Sprachmodellen in Software-Architekturen](../sprachmodell-integration.md)

KI-gestützte Dokumentationspflege, automatische PR-Reviews, Konsistenzprüfung, API-Dokumentensynthese und deterministische Builds.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Vale](https://github.com/errata-ai/vale) | MIT | Sehr hoch | Regelbasierter Stilprüfer als Ergänzung zur KI-gestützten Textarbeit. | Dateien: [Geprüfte Textdateien und lokale Stilregeln](https://vale.sh/) |
| 2 | [Aider](https://github.com/Aider-AI/aider) | Apache-2.0 | Hoch | Ausgereifter Terminal-Assistent zur iterativen Bearbeitung von Repositories und Git-Commits. | Dateien: [Repository-Dateien und Chat-Historie](https://aider.chat/docs/config/options.html) |
| 3 | [Cline](https://github.com/cline/cline) | Apache-2.0 | Hoch | Autonomer Repository-Agent für mehrstufige Dokumentenänderungen und Build-Prüfung. | Dateien: [Repository-Inhalte und JSON-Trajektorien](https://docs.cline.bot/sdk/clinecore) |
| 4 | [mini-SWE-agent](https://github.com/SWE-agent/mini-swe-agent) | MIT | Mittel | Schlanker Agent für automatisierte Fehlerbehebung und Aktualisierung in Code-Repositories. | Dateien: [Repository-Dateien und JSON-Trajektorien](https://mini-swe-agent.com/v2/usage/mini/) |
| 5 | [Gemini CLI](https://github.com/google-gemini/gemini-cli) | Apache-2.0 | Mittel | Open-Source-CLI für automatisierte Dokumentenanalysen und dateibasierte Sitzungen. | Dateien: [Repository-Inhalte und lokale Sitzungsdaten](https://geminicli.com/docs/cli/session-management/) |

## Einsatz und Abgrenzung

Docs-as-Code erfordert strikte Trennung zwischen kreativer KI-Generierung und reproduzierbarem Build.

- **Vale:** Prüft Text anhand konfigurierter Regeln; wird hier als ergänzender Linter und nicht als Sprachmodell bewertet.
- **Aider:** Bearbeitet Dateien direkt im Arbeitsverzeichnis; Entwickler behalten die Kontrolle über den Git-Diff.
- **Cline:** Erlaubt mehrstufige agentische Änderungen; erfordert anschließenden Build-Test (z. B. `mdbook build`).
- **mini-SWE-agent:** Bietet automatisierte Korrekturläufe; Benchmarkergebnisse ersetzen kein fachliches Review.
- **Gemini CLI:** Bearbeitet lokale Repository-Dateien; Anmeldung und Modellzugriff hängen vom gewählten Anbieter ab.
