# Terminal-Schleifen, Test-Runner und Workspace-Sandboxing

[Übergeordnete Kategorie: IDEs, Code-Editoren und KI-Framework-SDKs](../ide-ki-integration.md)

Moderne Entwicklungsumgebungen beschränken sich nicht auf das passive Bearbeiten von Quellcode. Sie integrieren interaktive Terminals, Debugger und Test-Runner. Autonome In-IDE-Agenten nutzen diese Werkzeuge über KI-Framework-SDKs, um Codeänderungen direkt gegen Compiler und automatisierte Test-Suiten zu validieren. Dieser mächtige Hebel birgt jedoch erhebliche Sicherheitsrisiken für das lokale Entwicklungssystem.

---

## Die autonome Test-Fix-Schleife (TDD-Agentur)

Anstatt den Entwickler als manuellen Tester einzuspannen, schließt das KI-SDK die Schleife zwischen Codeänderung und Feedback selbstständig:

```
┌─────────────────────────────────────────────────────────────┐
│ 1. KI-SDK modifiziert Quellcode im Editor-Puffer           │
└──────────────────────────────┬──────────────────────────────┘
                               │
┌──────────────────────────────▼──────────────────────────────┐
│ 2. IDE-Terminal führt Test-Runner aus                       │
│    Befehl: `cargo test` / `pytest` / `npm test`             │
└──────────────────────────────┬──────────────────────────────┘
                               │
               ┌───────────────┴───────────────┐
               │ Test erfolgreich (Exit 0)?    │
               ▼                               ▼
       [Nein: Exit > 0]                 [Ja: Exit 0]
               │                               │
┌──────────────▼──────────────┐                ▼
│ 3. Stacktrace-Analyse       │    ┌──────────────────────────┐
│    SDK parst Terminal-Fehler│    │ 4. Aufgabe abgeschlossen │
│    und Zeilennummern        │    │    Entwickler informieren│
└──────────────┬──────────────┘    └──────────────────────────┘
               │ Gezielter Reparatur-Patch
               └───────────────► Zurück zu Schritt 1 (max. 4 Zyklen)
```

### Vorteile der Test-Runner-Kopplung:
1. **Verifikation vor Entwicklersichtung:** Der Entwickler wird erst dann über eine fertige Implementierung benachrichtigt, wenn alle Unit- und Integrationstests grün sind.
2. **Präzise Fehlerlokalisierung:** Durch das Parsen des Terminal-Outputs erhält das Modell die exakte Assertion-Fehlermeldung (z. B. `expected 200 OK, got 403 Forbidden`) und den Ausführungspfad des Stacktraces.

---

## Workspace-Sandboxing und Schutz vor bösartigen Repositories

Erhält ein KI-SDK die Erlaubnis, im Terminal beliebige Shell-Befehle auszuführen, verwandelt sich ein infiziertes Quellcode-Repository (z. B. durch versteckte Prompts in Quelltext-Kommentaren oder Issue-Beschreibungen) in einen Angriffsvektor (Prompt-Injection):

### Technische Schutzvorkehrungen in der IDE:
* **Workspace Trust:** Beim Öffnen unbekannter Repositories schaltet die IDE standardmäßig in den eingeschränkten Modus. Automatische Terminal-Ausführungen und unbestätigte Dateimodifikationen sind hardwarenah gesperrt.
* **Befehls-Whitelisting und -Blacklisting:**
  * **Erlaubt:** Reine Diagnose- und Testbefehle (`pytest`, `npm test`, `git diff`, `cargo check`).
  * **Strikt gesperrt:** Zerstörerische oder sicherheitskritische Befehle (`rm -rf`, Manipulation von `.git/hooks`, Zugriff auf private SSH-Schlüssel in `~/.ssh` oder Manipulation von Netzwerkinterfaces).
* **Containerisierte Ausführung:** Testläufe und Skripte sollten bevorzugt in isolierten Umgebungen (z. B. Docker-Containern oder Linux-Namespaces) ausgeführt werden, um das Host-Dateisystem vor ungewollten Nebeneffekten zu schützen.
* **Human-in-the-Loop-Freigaben:** Vor dem Ausführen von Befehlen mit dauerhafter Außenwirkung (z. B. Paketinstallationen wie `npm install` oder Datenbankmigrationen) muss die IDE zwingend eine explizite Bestätigung im UI vom Entwickler anfordern.

---

## Projektweite Konfigurationsdateien (`AGENTS.md`, `.cursorrules`)

Um das Verhalten des KI-SDKs im Projekt deterministisch zu steuern, hinterlegen Entwicklungsteams verbindliche Konfigurationsdateien im Wurzelverzeichnis des Repositories:

* **Stil- und Framework-Vorgaben:** Definition erlaubter Bibliotheken und verbotener Hilfsfunktionen.
* **Build- und Test-Konventionen:** Exakte Angabe, welche Test-Kommandos vor dem Abschluss einer Aufgabe auszuführen sind.
* **Rechtliche und redaktionelle Richtlinien:** Vorgaben zur Einhaltung von Urheberrechten, Dokumentationsintegrität und Vermeidung von redundanten Code-Dubletten.

---

> [!NOTE]
> Die allgemeinen Kriterien zur Softwareauswahl und die Bewertung offener Editoren finden sich unter [Sprachmodelle in IDEs und Code-Editoren](sprachmodelle/ide-code-editoren.md) und [Softwareauswahl und Reifegrade](../software.md).
