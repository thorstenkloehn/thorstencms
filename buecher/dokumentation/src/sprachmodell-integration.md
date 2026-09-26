# Integration von Sprachmodellen in Software-Architekturen

Ein Sprachmodell kann einen Textentwurf erzeugen, Informationen aus bereitgestellten
Passagen zusammenfassen oder einen Werkzeugaufruf vorschlagen. Die umgebende
Anwendung entscheidet, welche Daten es erhält und welche Aktionen tatsächlich
ausgeführt werden. Diese Trennung ist für überprüfbare Ergebnisse wichtig.

## Beispiel: Eine Antwort aus einem Handbuch

Eine Nutzerin fragt nach einer Konfigurationsoption. Die Anwendung sucht
relevante Handbuchpassagen, prüft deren Zugriffsrechte und gibt sie zusammen
mit der Frage an das Modell. Der Antwortentwurf enthält Verweise auf die
verwendeten Stellen. Fehlende oder widersprüchliche Informationen müssen
sichtbar bleiben, statt durch eine plausible Vermutung ersetzt zu werden.

Auch ein RAG-System kann falsche Antworten erzeugen. Ein Quellenlink belegt
erst dann eine Aussage, wenn die verlinkte Passage sie tatsächlich stützt.
Die Qualität hängt unter anderem von Dokumentbestand, Abruf, Modell und
Prüfung ab. Vektorsuche allein verhindert keine Halluzinationen.

## Integrationsorte

| Bereich | Möglicher Ablauf | Zusätzliche Aufgabe der Anwendung |
| --- | --- | --- |
| CMS | Entwurf oder Metadaten vorschlagen | Redaktionelle Freigabe und Änderungshistorie |
| Webanwendung | Antwort schrittweise anzeigen | Anmeldung, Zeitlimits und Fehlerbehandlung |
| LMS | Rückmeldung zu einer Übung vorbereiten | Didaktische Prüfung und Schutz der Lerndaten |
| Wissenssystem | Passagen suchen und zusammenfassen | Zugriffsrechte und nachvollziehbare Belege |
| Docs-as-Code | Änderungsvorschlag an Textdateien erzeugen | Diff-Prüfung und anschließender Build |
| Office-Editor | Markierten Text umarbeiten | Bewusste Auswahl des Modellanbieters und der übertragenen Inhalte |

## Daten und Werkzeugaufrufe

PostgreSQL kann Dokumente, Metadaten und Konversationszustand speichern.
Für Vektoren kommt eine passende Erweiterung oder Integration hinzu.
Ein PostgreSQL-Vektorspeicher ist dabei nicht automatisch ein Speicher für
den gesamten Agentenzustand. Jede Datenart braucht eine klare Zuordnung.

Ein Modellvorschlag für einen Werkzeugaufruf wird von Anwendungscode geprüft.
Ein passendes JSON-Schema kontrolliert die Form, nicht die fachliche Richtigkeit
oder Berechtigung. Die Anwendung muss Zugriff und zulässige Parameter zusätzlich
prüfen, bevor sie eine Aktion ausführt.

## Lokale und externe Modelle

Ollama kann Modelle lokal ausführen und bietet auch Cloud-Funktionen.
Für eine lokale Verarbeitung müssen Modellwahl und Konfiguration dazu passen;
zusätzliche Werkzeuge dürfen Inhalte nicht unbeabsichtigt weiterleiten.
[Ollama: Lokaler Betrieb und Cloud-Funktionen](https://docs.ollama.com/faq).

Die Lizenz einer Laufzeit oder Bibliothek gilt nicht automatisch für die
Modellgewichte. Hardwarebedarf, Nutzungsrechte und Datenflüsse werden deshalb
getrennt beurteilt. Ein lokaler Server garantiert noch keine Datenschutzkonformität.

## Unterkategorien: gefilterte Softwareauswahl

- [CMS-Anbindung](sprachmodelle/cms.md)
- [Webframeworks und Backend](sprachmodelle/frameworks.md)
- [Bibliotheken und Laufzeiten](sprachmodelle/bibliotheken.md)
- [Lernmanagement-Systeme](sprachmodelle/lms.md)
- [Docs-as-Code](sprachmodelle/docs-as-code.md)
- [Wissenssysteme](sprachmodelle/wissenssysteme.md)
- [IDEs und Code-Editoren](sprachmodelle/ide-code-editoren.md)
- [Office- und Autorentools](sprachmodelle/office-autorentools.md)

## Open-Source-Auswahl nach Reifegrad

**4 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: 27. September 2026. Auswahl nach der
[gemeinsamen Bewertungsmethode](software.md). Die Reihenfolge priorisiert
Reife und anschließend die Eignung für diese Kategorie.

| Rang | Software | Lizenz des Kerns | Reifegrad | Schwerpunkt | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [LangChain](https://github.com/langchain-ai/langchain) | MIT | Hoch | Umfassende Modell-Orchestrierung und Tool-Chains | PostgreSQL: [Dokument- und Vektorspeicher über langchain-postgres](https://github.com/langchain-ai/langchain-postgres) |
| 2 | [LlamaIndex](https://github.com/run-llama/llama_index) | MIT | Hoch | Daten-Framework für Dokumenten-Indizierung und RAG | PostgreSQL: [PGVectorStore-Integration](https://developers.llamaindex.ai/python/framework-api-reference/storage/vector_store/postgres/) |
| 3 | [Ollama](https://github.com/ollama/ollama) | MIT | Hoch | Lokale Laufzeitumgebung für Open-Weights-Sprachmodelle | Dateien: [Lokale Modell- und GGUF-Dateien](https://ollama.com/) |
| 4 | [LiteLLM](https://github.com/BerriAI/litellm) | MIT | Hoch | Zentrales Gateway und Proxy für 100+ Modellanbieter | PostgreSQL: [PostgreSQL für Proxy-Schlüssel und Budgets](https://docs.litellm.ai/docs/proxy/virtual_keys) |

## Betrieb und Prüfung

LangChain und LlamaIndex sind Integrationsbibliotheken. Eine Oberfläche,
Berechtigungen und Evaluationsfälle gehören zur eigenen Anwendung. LiteLLM
kann Modellzugriffe bündeln; die ausgewählte Variante verwendet PostgreSQL
für den Proxy-Zustand. Ollama wird hier als Laufzeit mit lokalen Modelldateien
betrachtet, nicht als fertiger Dokumentenspeicher.

Für eine neue Anwendung helfen einige bewusst schwierige Prüffragen:
Was passiert ohne passenden Beleg? Werden veraltete Passagen erkannt?
Kann ein Benutzer Inhalte aus einem gesperrten Kurs abrufen? Bleiben Fehler
bei Modell- oder Werkzeugaufrufen sichtbar? Solche Tests müssen zur konkreten
Anwendung gehören und wurden hier nicht für die genannten Produkte durchgeführt.

[CLI-Agenten](cli-agenten.md) und [App-Architekturen](mobile-desktop-apps.md)
vertiefen die Nutzung dieser Bausteine im Arbeitsalltag.
