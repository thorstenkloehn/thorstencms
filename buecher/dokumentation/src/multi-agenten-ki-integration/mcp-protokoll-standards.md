# Das Model Context Protocol (MCP) und Schnittstellenstandards

[Übergeordnete Kategorie: Multi-Agenten-Systeme und Protokolle](../multi-agenten-ki-integration.md)

Vor der Einführung offener Protokolle glich die Anbindung von Werkzeugen an KI-Modelle einem $M \times N$-Integrationsproblem: Jeder Agenten-Entwickler und jeder IDE-Hersteller musste eigene, herstellerspezifische Schnittstellen für GitHub, PostgreSQL, Slack oder Dateisysteme programmieren. Das von Anthropic initiierte und als offener Industriestandard geführte **Model Context Protocol (MCP)** löst dieses Problem durch eine standardisierte Client-Server-Architektur auf Basis von JSON-RPC 2.0.

---

## Architektur und Komponenten von MCP

MCP trennt die Ausführungsebene des Modells strikt von der Bereitstellung von Daten und Werkzeugen:

```
┌─────────────────────────────────────────────────────────────┐
│                       MCP-Host                              │
│       (IDE, Antigravity, Claude Desktop, Agent-Service)     │
│                                                             │
│   ┌────────────────────┐            ┌───────────────────┐   │
│   │ MCP-Client 1       │            │ MCP-Client 2      │   │
└─────┬──────────────────┴──────────────┬───────────────────┴───┘
      │ stdio (Lokaler Prozess)          │ SSE / HTTP (Netzwerk)
      ▼                                  ▼
┌────────────────────────┐         ┌────────────────────────┐
│ MCP-Server: Filesystem │         │ MCP-Server: PostgreSQL │
│ (Liest lokale Dateien, │         │ (Führt Abfragen aus,   │
│  erstellt Verzeichnisse│         │  liefert Datenbankschem│
└────────────────────────┘         └────────────────────────┘
```

### Die drei Funktionsträger:
1. **MCP-Host:** Die übergeordnete Anwendung, die den Benutzerkontext verwaltet und das Sprachmodell instanziiert.
2. **MCP-Client:** Eine Protokollinstanz innerhalb des Hosts, die eine exklusive 1:1-Verbindung zu einem bestimmten MCP-Server unterhält.
3. **MCP-Server:** Ein isolierter, spezialisierter Prozess, der Zugriff auf eine konkrete Ressource (Dateisystem, Datenbank, Git-Repository, Web-Scraper) gewährt.

---

## Die drei Kernprimitiven von MCP

Ein MCP-Server deklariert seine Fähigkeiten gegenüber dem Client über drei standardisierte Primitiven:

### 1. Resources (Kontextdaten zum Lesen)
Resources sind passive, datei- oder dokumentenähnliche Datenquellen. Sie verändern den Systemzustand nicht und können sicher gelesen werden:
* **URI-basiertes Schema:** z. B. `file:///workspace/src/main.rs` oder `postgres://analytics/tables/users/schema`.
* **Subskriptionen:** MCP-Clients können Ressourcen abonnieren und werden vom Server automatisch per Push benachrichtigt, wenn sich eine Quelldatei ändert.

### 2. Tools (Ausführbare Funktionen mit Nebeneffekten)
Tools sind aktive Funktionen, die das Sprachmodell aufrufen kann, um Operationen auszuführen:
* **Typsichere Deklaration:** Jedes Tool definiert seinen Namen, eine präzise Beschreibung und seine Eingabeparameter über ein standardisiertes JSON-Schema.
* **Ergebnisrückgabe:** Nach der Ausführung liefert das Tool strukturierte Text- oder Bilddaten an den Agenten zurück.

### 3. Prompts (Vordefinierte Interaktionsmuster)
Prompts sind wiederverwendbare, vom Server bereitgestellte Vorlagen:
* Ein Git-MCP-Server kann beispielsweise einen Prompt `generate_release_notes` bereitstellen, der vordefinierte Kontextparameter wie Tags oder Commit-Spannen abfragt.

---

## Transportprotokolle: stdio vs. SSE

MCP definiert zwei verbindliche Transportmechanismen:

| Kriterium | Standard-I/O (`stdio`) | Server-Sent Events (`SSE`) über HTTP |
| :--- | :--- | :--- |
| **Betriebsort** | Lokale Prozesse auf demselben Rechner | Verteilte Server, Container oder Cloud-Dienste |
| **Kommunikation** | Standard-Input/Output-Streams des OS-Prozesses | HTTP-Post-Anfragen mit asynchronem SSE-Stream |
| **Latenz** | Extrem gering (< 1 ms); keine Netzwerk-Overheads | Gering; abhängig von der Netzwerklatenz |
| **Sicherheit** | Prozessisolation über Betriebssystem-Rechte | Authentifizierung über HTTPS, API-Tokens oder mTLS |
| **Typischer Einsatz** | Lokale IDE-Werkzeuge, Dateisystem-Zugriff | Unternehmensdatenbanken, Cloud-APIs, Microservices |

Durch diese Trennung kann derselbe MCP-Server für PostgreSQL sowohl von einem lokalen Entwickler im Terminal als auch von einem serverseitigen Multi-Agenten-Workflow im Rechenzentrum genutzt werden.

---

> [!NOTE]
> Wie mehrere Agenten untereinander koordiniert werden und welche Topologien sich in der Praxis bewährt haben, zeigt die Unterkategorie [Agenten-Topologien, Koordination und Rollenmodelle](topologien-orchestrierung.md).
