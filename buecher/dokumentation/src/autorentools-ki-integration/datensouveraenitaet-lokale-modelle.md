# Vertraulichkeit, Manuskriptschutz und lokale Inferenz

[Übergeordnete Kategorie: Autorentools und KI-Framework-SDKs](../autorentools-ki-integration.md)

Unveröffentlichte Buchmanuskripte, juristische Verträge, journalistische Recherchen und wissenschaftliche Vorab-Veröffentlichungen (Preprints) gehören zu den vertraulichsten Datenbeständen überhaupt. Bei der Arbeit in Autorentools riskieren Verfasser durch die leichtfertige Nutzung cloudbasierter KI-Erweiterungen Vertragsstrafen, den Verlust von Urheberrechten oder die Gefährdung von Informanten.

---

## Das Risiko cloudbasierter Schreibassistenten

Viele handelsübliche Schreibhelfer übertragen jeden eingegebenen Tastaturanschlag oder jeden markierten Absatz unverschlüsselt an Serverbetreiber:

* **Bruch von Geheimhaltungsvereinbarungen (NDAs):** Autoren verstoßen gegen Vereinbarungen mit Verlagen oder Mandanten, wenn Entwürfe auf fremde Rechenzentren hochgeladen werden.
* **Ungewolltes Modelltraining:** Sofern keine gesonderten Enterprise-Vereinbarungen mit „Zero Data Retention“-Klauseln vorliegen, behalten sich viele Anbieter das Recht vor, übermittelte Texte zum Nachtrainieren zukünftiger Modellgenerationen zu nutzen. Vertrauliche Handlungswendungen oder noch unveröffentlichte Forschungsergebnisse können so in Antworten für Dritte einfließen.
* **Verlust der Offline-Fähigkeit:** Viele Autoren arbeiten bewusst fernab von Internetverbindungen (z. B. auf Reisen oder in Rückzugsphasen). Cloud-gebundene Assistenten versagen in solchen Umgebungen vollständig.

---

## Lokale Inferenz auf dem Autoren-Rechner (Local-First)

Die nachhaltige architektonische Antwort für Autorentools ist die vollständige Entkopplung von externen Netzwerken durch **lokale Open-Weights-Modelle**:

```
┌─────────────────────────────────────────────────────────────┐
│ Autoren-Arbeitsplatz (Vollständig Offline / Air-Gapped)     │
│                                                             │
│  ┌───────────────────────┐         ┌─────────────────────┐  │
│  │ Autorentool / Editor  │         │ Lokale Modell-Engine│  │
│  │ (OnlyOffice, Obsidian,├────────►│ (Ollama / llama.cpp)│  │
│  │  Zettlr, Typora)      │ HTTP    │ Quantisiertes GGUF  │  │
│  └───────────────────────┘ 127.0.0.1 └─────────────────────┘  │
│             │                                               │
│             ▼                                               │
│  [Lokales Dateisystem: Manuskript als Markdown / DOCX]      │
└─────────────────────────────────────────────────────────────┘
  Kein Datenfluss über das Internet – 100 % Datensouveränität
```

### Technische Laufzeiten für Desktop-Systeme:
1. **Ollama:** Läuft als schlanker Hintergrunddienst auf dem Betriebssystem und stellt eine OpenAI-kompatible HTTP-Schnittstelle unter `http://localhost:11434` bereit. KI-Plugins können dieselben Standard-SDKs verwenden, leiten die Anfragen jedoch auf den lokalen Host um.
2. **llama.cpp und quantisierte GGUF-Modelle:** Erlauben die Ausführung leistungsfähiger Modelle mit 4-Bit- oder 8-Bit-Quantisierung direkt auf handelsüblichen Laptops. Auf modernen Prozessoren (insbesondere Apple Silicon oder x86-CPUs mit AVX2) erreichen diese Modelle Inferenzgeschwindigkeiten von 30 bis 60 Tokens pro Sekunde – ideal für flüssigen Ghost-Text.
3. **In-Process-Engines (ONNX Runtime):** Das Modell wird als native Programmbibliothek direkt in den Editor eingebettet, ohne dass der Benutzer einen separaten Hintergrunddienst konfigurieren muss.

---

## Transparenz und Sicherheits-Indikatoren in der Benutzeroberfläche

Ein professionelles Autorentool muss dem Schreibenden zu jedem Zeitpunkt unmissverständlich signalisieren, wohin Textdaten fließen:

* **Visuelle Status-Ampel:**
  * **Grünes Schild („Lokal“):** Modell läuft vollständig offline auf der lokalen Hardware. Keine Internetkommunikation.
  * **Blaues Schild („Enterprise Cloud“):** Verbindung zu einem vertraglich abgesicherten API-Endpunkt mit garantierter Datenlöschung und ohne Modelltraining.
  * **Warnhinweis („Public Cloud“):** Nutzung eines externen Verbraucherdienstes; Warnung vor dem Einfügen sensibler Passagen.
* **Manuskript-Schutzflags:** In den Dokumenteneigenschaften kann der Autor das Flag `Vertraulich` setzen. In diesem Modus sperrt das Editor-Plugin alle externen Netzwerkaufrufe hardwarenah und erlaubt ausschließlich lokale Inferenz-Engines.

---

> [!NOTE]
> Die allgemeinen Kriterien zur Softwareauswahl und die Grenzen dokumentierter Lösungen finden sich unter [Softwareauswahl und Reifegrade](../software.md).
