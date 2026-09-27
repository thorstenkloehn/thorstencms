# Persistente Zustandsgraphen, Time-Travel und Human-in-the-Loop

[Übergeordnete Kategorie: Multi-Agenten-Systeme und Protokolle](../multi-agenten-ki-integration.md)

Ein komplexer Multi-Agenten-Workflow umfasst oft Dutzende Zwischenschritte: Recherche, Architekturentwurf, Codierung, Kompilierung und Review. Läuft ein solcher Prozess rein im flüchtigen Arbeitsspeicher ab, führt jeder Netzwerkabbruch, jeder Serverneustart oder jedes API-Ratenlimit zum vollständigen Verlust des bisherigen Fortschritts. 

Professionelle Multi-Agenten-Architekturen verlangen deshalb **persistente Zustandsverwaltung (Checkpointing)** und die Möglichkeit, Workflows kontrolliert anzuhalten (**Human-in-the-Loop**).

---

## Das Checkpointing-Prinzip mit PostgreSQL

In graphbasierten Frameworks wie [LangGraph](https://github.com/langchain-ai/langgraph) wird nach der Ausführung jedes einzelnen Knotens ein unveränderlicher Snapshot des globalen Zustands in einer relationalen Datenbank persistiert:

```
[Knoten 1: Recherche] ──► Snapshot 1 (PostgreSQL `checkpoints`)
          │
          ▼
[Knoten 2: Entwurf]   ──► Snapshot 2 (PostgreSQL `checkpoints`)
          │
          ▼
[Knoten 3: Code-Erstellung] ──► Snapshot 3 (PostgreSQL `checkpoints`)
          │
   [SERVER-ABSTURZ / PROZESS-TIMEOUT]
          │
          ▼
[Neustart: Graph lädt Snapshot 3 via `thread_id` und setzt nahtlos fort]
          │
          ▼
[Knoten 4: Testausführung]
```

### Technische Umsetzung:
1. **Thread-Identifikatoren:** Jeder Workflow wird über eine eindeutige Sitzungs-ID (`thread_id`) identifiziert.
2. **Serialisierung des Zustands:** Der globale Graph-Zustand (enthaltene Nachrichten, extrahierte Variablen, bearbeitete Dateipfade) wird in strukturierte JSON- oder Binärformate serialisiert.
3. **Ausfallsicherheit:** Tritt bei Schritt 8 ein Fehler auf, muss das System die Schritte 1 bis 7 nicht erneut ausführen und spart dadurch erhebliche Inferenzkosten und Wartezeiten.

---

## Time-Travel-Debugging und Trajektorien-Replay

Da jeder Zustandsschritt persistent mit Versionsnummer und Zeitstempel in PostgreSQL gespeichert wird, eröffnen sich mächtige Debugging-Möglichkeiten:

* **Historische Inspektion:** Entwickler können den exakten Zustand des Systems zu jedem beliebigen Zeitpunkt der Vergangenheit analysieren (*„Welche Argumente hatte Agent B in Schritt 4 an das Werkzeug übergeben?“*).
* **Zustandsgabelung (Forking & Time-Travel):** Hat ein Agent in Schritt 5 eine falsche Annahme getroffen, muss der Workflow nicht von Grund auf neu gestartet werden. Der Entwickler lädt den Snapshot von Schritt 4, korrigiert den fehlerhaften Parameter manuell und startet die Ausführung ab diesem Punkt in einem neuen Ausführungszweig.

---

## Human-in-the-Loop: Geplante Unterbrechungen (Interrupts)

Vollautonome Agenten bergen bei sicherheitskritischen Aktionen unkalkulierbare Risiken. Durch gezielte **Haltepunkte (Interrupts)** erzwingt der Graph die menschliche Freigabe:

```python
# Konfiguration eines LangGraph-Zustandsgraphen mit Haltepunkt
app = workflow.compile(
    checkpointer=postgres_checkpointer,
    interrupt_before=["deploy_to_production", "drop_database_table"]
)
```

### Der Ablauf bei einem Haltepunkt:
1. **Automatisches Pausieren:** Erreicht der Kontrollfluss die Kante vor dem Knoten `deploy_to_production`, stoppt der Graph die Ausführung selbstständig.
2. **Statusmeldung an das UI:** Das System persistiert den Zustand und meldet dem Frontend: *„Aktion erfordert Freigabe: Soll Version 2.4 auf den Produktionsserver aufgespielt werden?“*
3. **Menschliche Entscheidung:**
   * **Freigabe (Approve):** Der Administrator bestätigt die Aktion; der Graph wird mit `resume()` fortgesetzt.
   * **Modifikation (Edit):** Der Administrator ändert die Zielumgebung auf den Staging-Server und setzt fort.
   * **Abbruch (Reject):** Der Vorgang wird gestoppt und der Agent über die Ablehnung informiert.

---

> [!NOTE]
> Die Anbindung an serverseitige Webframeworks und Hintergrund-Queues zur Bereitstellung dieser Kontrolloberflächen wird im Kapitel [Webframeworks und KI-Framework-SDKs](web-ki-integration.md) vertieft.
