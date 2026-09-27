# Sichere Werkzeugausführung und Sandboxing

[Übergeordnete Kategorie: Webframeworks und KI-Framework-SDKs](../web-ki-integration.md)

Moderne Sprachmodelle und KI-Frameworks beschränken sich nicht auf die reine Textgenerierung, sondern können über Werkzeugaufrufe (Tool Calling bzw. Function Calling) externe Systeme ansteuern. Sie können Datenbanken abfragen, Dokumente durchsuchen oder APIs bedienen. Da Sprachmodelle jedoch probabilistisch arbeiten und durch Manipulation von Kontextdaten (Prompt-Injection) fehlgeleitet werden können, stellt die unkontrollierte Ausführung von Werkzeugaufrufen ein erhebliches Sicherheitsrisiko dar.

---

## Das Drei-Stufen-Modell der kontrollierten Ausführung

Ein Sprachmodell darf niemals direkten Zugriff auf Systembefehle oder Datenbankverbindungen erhalten. Das Webframework agiert als isolierende Kontrollinstanz:

```
┌─────────────────────────────────────────────────────────────┐
│ 1. Modell-Vorschlag (KI-Framework-SDK)                      │
│    Erzeugt rein textuelles JSON: {"tool": "x", "args": {}}  │
└──────────────────────────────┬──────────────────────────────┘
                               │ Vorschlag abfangen
┌──────────────────────────────▼──────────────────────────────┐
│ 2. Webframework-Interzeption & Validierung                  │
│    ├─ Prüfung gegen Pydantic-/Zod-Schema (Typen, Werte)     │
│    └─ Autorisierung gegen Benutzer-Session (RBAC / Tenant)  │
└──────────────────────────────┬──────────────────────────────┘
                               │ Berechtigte Parameter
┌──────────────────────────────▼──────────────────────────────┐
│ 3. Isolierte Ausführung (Sandbox im Backend)                │
│    ├─ Ausführung mit Minimalrechten (Least Privilege)       │
│    ├─ Zeitlimitierung (Execution Timeouts)                  │
│    └─ SSRF-Schutz (Blockade interner IP-Netze)              │
└─────────────────────────────────────────────────────────────┘
```

### Stufe 1: Formale Schemadefinition
Werkzeuge werden dem Modell über strikte Schemata (z. B. über Pydantic in Python oder Zod in TypeScript) deklariert. Das Modell erzeugt lediglich einen strukturierten Textvorschlag im JSON-Format, der den gewünschten Funktionsnamen und die Parameter enthält.

### Stufe 2: Interzeption und Rechteprüfung im Webframework
Das Webframework fängt diesen Vorschlag vor der Ausführung ab:
* **Syntaktische Validierung:** Entsprechen die Argumente exakt den definierten Datentypen und Wertebereichen?
* **Kontextbezogene Autorisierung:** Besitzt der aktuell eingeloggte Benutzer überhaupt die Berechtigung, die angeforderte Aktion für den angegebenen Datensatz auszuführen? Ein Mandant darf niemals über einen vom Modell generierten Parameter auf Daten fremder Mandanten zugreifen (Schutz vor IDOR – Insecure Direct Object References).

### Stufe 3: Isolierte Ausführung (Sandboxing)
Wird der Aufruf freigegeben, führt das Backend ihn unter strengen Schutzvorkehrungen aus:
* **Least Privilege:** Datenbankabfragen über KI-Werkzeuge sollten über dedizierte Datenbankbenutzer laufen, die ausschließlich Lesezugriff auf explizit freigegebene Tabellen und Sichten besitzen.
* **Schutz vor Server-Side Request Forgery (SSRF):** Wenn das Modell URLs für Web-Recherchen anfordert, muss das Webframework Zugriffe auf private Netzwerkbereiche (wie `localhost`, interne Subnetze oder Cloud-Metadaten-Endpunkte wie `169.254.169.254`) strikt blockieren.
* **Ausführungs-Timeouts:** Jede Werkzeugausführung muss mit einem harten Timeout versehen werden, um Blockaden durch langsame externe Dienste abzufangen.

---

## Human-in-the-Loop für Aktionen mit Außenwirkung

Nicht jede Aktion darf vollautomatisch ausgeführt werden. Bei Operationen mit irreversiblen Folgen (z. B. das Löschen von Datensätzen, das Auslösen von Zahlungsvorgängen oder der Versand von E-Mails) ist ein **Human-in-the-Loop-Muster** unverzichtbar:

1. **Unterbrechung (Interrupt):** Das KI-Framework (z. B. über Checkpoints in LangGraph) pausiert die Ausführungskette vor dem kritischen Schritt und speichert den Zwischenzustand in PostgreSQL.
2. **Bestätigungsanforderung an das UI:** Das Webframework sendet eine strukturierte Bestätigungsanfrage an den Client: *„Das Modell möchte folgende E-Mail an Empfänger X senden. Möchten Sie diesen Vorgang freigeben?“*
3. **Freigabe und Wiederaufnahme:** Erst wenn der Benutzer die Aktion im Webinterface explizit bestätigt, wird der Zwischenzustand geladen, die Aktion ausgeführt und das Ergebnis an den Workflow zurückgemeldet.

---

> [!NOTE]
> Die theoretische Einordnung und die Kriterien zur Unterscheidung von Provider-SDKs und übergeordneten Frameworks sind im Kapitel [KI-Integrations- und Modellbibliotheken](../sprachmodelle/bibliotheken.md) dokumentiert.
