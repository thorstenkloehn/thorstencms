# Mobile und Desktop-Apps und KI-Framework-SDKs

Mobile Endgeräte (Smartphones, Tablets) und Desktop-Computer stellen Entwickler von KI-Anwendungen vor völlig andere Rahmenbedingungen als Cloud-Server. Während serverseitige Backend-Dienste über nahezu unbegrenzte Rechenleistung, redundante Stromversorgung und hochbitratige Netzwerkanbindungen verfügen, unterliegen Apps auf Endgeräten harten physikalischen Beschränkungen:

* **Begrenzter Arbeitsspeicher und thermische Budgets:** Auf Mobilgeräten stehen für Apps selten mehr als 2 bis 6 Gigabyte RAM zur Verfügung; dauerhafte Volllast führt zur Überhitzung (Thermal Throttling) und drastischem Akkuschwund.
* **Instabile und abwesende Netzwerkverbindungen:** Apps werden in Funklöchern, Flugzeugen oder gesicherten Unternehmensnetzen betrieben. Die Erwartungshaltung der Anwender verlangt, dass Kernfunktionen auch ohne Internetverbindung (Local-First) verfügbar bleiben.
* **Heterogene Hardware-Beschleuniger:** Vom Apple Neural Engine (ANE) auf iOS und macOS über Qualcomms NPU auf Android-Geräten bis hin zu dedizierten Grafikkarten (Nvidia, AMD, Intel) auf Desktop-Systemen existiert eine unübersichtliche Vielfalt an Ausführungseinheiten.

```
┌─────────────────────────────────────────────────────────────┐
│                 Mobile- / Desktop-App (UI)                  │
│       (Tauri, Swift/SwiftUI, Kotlin/Compose, Flutter)       │
└──────────────────────────────▲──────────────────────────────┘
                               │ Lokale Funktionsaufrufe
┌──────────────────────────────▼──────────────────────────────┐
│ Hybride KI-Routing-Schicht (Framework-SDK)                  │
│  ├─ Kontext-Erkennung (Netzwerkstatus, Akkustand, Aufgabe)  │
│  ├─ Routing-Entscheidung: Edge-Modell vs. Cloud-Inferenz    │
│  └─ Lokale Vektorabfrage & CRDT-Zustandsverwaltung          │
└──────────────────────────────▲──────────────────────────────┘
                               │
         ┌─────────────────────┴─────────────────────┐
         ▼                                           ▼
┌─────────────────────────────────┐ ┌─────────────────────────────────┐
│ On-Device-Inferenz (Offline)    │ │ Cloud-Backend (Online / HTTPS)  │
│  ├─ CoreML / ExecuTorch / ONNX  │ │  ├─ LiteLLM Gateway / Server    │
│  ├─ Quantisierte Modelle (4-Bit)│ │  ├─ PostgreSQL / pgvector       │
│  └─ Eingebettetes sqlite-vec    │ │  └─ Leistungsstarke RAG-Pipelines│
└─────────────────────────────────┘ └─────────────────────────────────┘
```

---

## Kernaufgaben der App-Integration

1. **On-Device-Hardwarebeschleunigung:** Nutzung nativer NPU- und GPU-APIs (CoreML, ExecuTorch, WebGPU), um quantisierte Sprachmodelle latenzarm und energieeffizient direkt auf dem Endgerät auszuführen.
2. **Local-First mit verzögerungsfreier Synchronisation:** Notizen, Wissensgraphen und semantische Indizes werden lokal gespeichert (z. B. über SQLite mit Vektorerweiterungen). Bei wiederkehrender Internetverbindung gleicht ein CRDT-gestützter Sync-Mechanismus den Stand mit dem zentralen PostgreSQL-Server ab.
3. **Asymmetrische Modellkaskadierung (Hybrid Routing):** Einfache Aufgaben (Textzusammenfassung, In-Line-Klassifizierung, UI-Steuerung) erledigt ein kompaktes lokales 2B-Modell offline; komplexe Synthesen werden bei stabiler WLAN-Verbindung an Cloud-Modelle delegiert.

---

## Unterkategorien dieses Kapitels

Die konkreten Implementierungsmuster gliedern sich in drei Schwerpunkte:

* [On-Device-Inferenz und Hardwarebeschleunigung](apps-ki-integration/on-device-hardwarebeschleunigung.md): Ausführung quantisierter Open-Weights-Modelle auf mobilen NPUs und Desktop-GPUs (CoreML, ExecuTorch, ONNX Runtime Mobile).
* [Local-First-Architekturen, Offline-RAG und CRDT-Sync](apps-ki-integration/local-first-offline-rag.md): Eingebettete Vektordatenbanken (`sqlite-vec`), Offline-RAG auf Endgeräten und konfliktfreie Datensynchronisation mit PostgreSQL.
* [Hybrid-Routing, Modellkaskadierung und Energiemanagement](apps-ki-integration/hybrid-routing-energiemanagement.md): Intelligente Lastverteilung zwischen Gerät und Server, Vermeidung von Überhitzung und Akkuschutz.

---

> [!NOTE]
> Die redaktionelle Bewertung von Plattformen und Frameworks für native Apps (wie Tauri oder Moodle App) findet sich im Kapitel [Mobile und Desktop-Apps in Content- und Wissenssystemen](mobile-desktop-apps.md).
