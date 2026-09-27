# Agenten-Topologien, Koordination und Rollenmodelle

[Übergeordnete Kategorie: Multi-Agenten-Systeme und Protokolle](../multi-agenten-ki-integration.md)

Wenn ein einzelnes Sprachmodell versucht, komplexe Aufgaben wie das Entwerfen einer Softwarearchitektur, das Schreiben von Code, das Ausführen von Tests und das Verfassen von Dokumentation in einem einzigen Durchlauf zu erledigen, tritt der Effekt der **Kontext-Verwässerung (Context Dilution)** ein: Das Modell verliert Randbedingungen aus den Augen und erzeugt oberflächliche Ergebnisse.

Multi-Agenten-Systeme teilen komplexe Vorhaben auf mehrere spezialisierte Instanzen auf. Wie diese Agenten miteinander interagieren, wird durch die gewählte **Orchestrierungs-Topologie** bestimmt.

---

## Die drei primären Orchestrierungs-Topologien

In der Softwarearchitektur haben sich drei grundlegende Organisationsmuster etabliert:

```
Topologie 1: Hierarchischer Supervisor
              ┌─────────────────────┐
              │  Supervisor Agent   │
              │  (Planung & Triage) │
              └──────────┬──────────┘
       ┌─────────────────┼─────────────────┐
       ▼                 ▼                 ▼
┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│ Rechercheur  │  │ Entwickler   │  │ Reviewer     │
└──────────────┘  └──────────────┘  └──────────────┘

Topologie 2: Peer-to-Peer (Konversationsnetzwerk)
┌──────────────┐                  ┌──────────────┐
│   Agent A    │◄────────────────►│   Agent B    │
└──────┬───────┘                  └───────┬──────┘
       ▲                                  ▲
       └────────────────►┌──────────────┐◄┘
                         │   Agent C    │
                         └──────────────┘

Topologie 3: Deterministischer Zustandsgraph (LangGraph)
[Start] ──► (Recherche-Knoten) ──► (Codierungs-Knoten)
                                          │
                                          ▼
                                   <Bedingte Kante: Tests OK?>
                                    ├─ Nein ──► (Fix-Knoten) ──┐
                                    │                          │
                                    └─ Ja ──► [Ende] ◄─────────┘
```

---

## Detaillierter Vergleich der Muster

### 1. Hierarchische Supervisor-Architektur
Ein zentraler Supervisor analysiert die Gesamtaufgabe, zerlegt sie in Teilziele und weist diese spezialisierten Worker-Agenten zu.
* **Funktionsweise:** Die Worker kommunizieren nicht direkt untereinander, sondern liefern ihre Teilergebnisse an den Supervisor zurück, der über den nächsten Schritt entscheidet.
* **Vorteile:** Klare Führung, zentrale Kosten- und Fortschrittskontrolle, geringes Risiko unproduktiver Diskussionen.
* **Nachteile:** Der Supervisor stellt einen potenziellen Engpass (Single Point of Failure) dar, wenn er Teilaufgaben fehlinterpretiert.

### 2. Peer-to-Peer-Konversationen (AutoGen / CrewAI)
Agenten agieren als gleichberechtigte Teilnehmer in einem gemeinsamen Diskussionsraum (Group Chat).
* **Funktionsweise:** Jeder Agent vertritt eine definierte Persona (z. B. Produktmanager, Programmierer, Sicherheitsauditor). Ein Moderator-Modell entscheidet anhand des Diskussionsverlaufs, wer als Nächstes antwortet.
* **Risiko von Endlosschleifen (Endless Chatter):** Ohne harte Abbruchbedingungen (Max Iterations oder explizite Termination-Tokens) neigen konversationsbasierte Systeme dazu, sich in Höflichkeitsfloskeln oder unproduktiven Detaildiskussionen zu verfangen.

### 3. Deterministische Zustandsgraphen (LangGraph)
Die flexibelste und robusteste Architektur für Unternehmensanwendungen modelliert Abläufe als **zyklische Zustandsgraphen**:
* **Knoten (Nodes):** Repräsentieren eigenständige Agenten, Python-Funktionen oder Werkzeugaufrufe, die den globalen Zustand manipulieren.
* **Kanten (Edges):** Steuern den Kontrollfluss. **Bedingte Kanten (Conditional Edges)** werten den aktuellen Zustand aus und leiten den Prozess deterministisch weiter (z. B. *„Wenn Testfehler > 0, verzweige zu Bugfix-Knoten, sonst zu Dokumentations-Knoten“*).
* **Zyklen:** Schleifen sind explizit erlaubt, wodurch iterative Nachbesserungen transparent abgebildet werden.

---

## Das Prinzip des Least Privilege bei Agenten-Rollen

Ein Kernvorteil spezialisierter Agenten liegt in der Beschränkung von Rechten:
* Ein **Recherche-Agent** erhält ausschließlich Lese-Werkzeuge (z. B. MCP-Server für Websuche und Dokumentations-Archive). Er besitzt keinerlei Schreibrechte auf Repositories oder Datenbanken.
* Ein **Entwicklungs-Agent** kann Dateien modifizieren und Test-Runner aufrufen, darf jedoch keine Git-Pushes auf Remotes durchführen.
* Ein **Sicherheits- und Review-Agent** verfügt über Linter- und Diff-Werkzeuge, besitzt jedoch keine Berechtigung, Code selbstständig umzuschreiben.

---

> [!NOTE]
> Wie der globale Zustand dieser Graphen zuverlässig in Datenbanken persistiert und bei Fehlern zurückgespult wird, vertieft die Unterkategorie [Persistente Zustandsgraphen, Time-Travel und Human-in-the-Loop](zustandsgraphen-human-in-the-loop.md).
