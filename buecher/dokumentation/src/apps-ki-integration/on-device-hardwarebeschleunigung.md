# On-Device-Inferenz und Hardwarebeschleunigung

[Übergeordnete Kategorie: Mobile und Desktop-Apps und KI-Framework-SDKs](../apps-ki-integration.md)

Auf modernen mobilen Endgeräten und Desktop-Computern erfolgt die Berechnung von KI-Modellen nicht mehr ausschließlich über die Hauptprozessoren (CPUs). Zeitgemäße SoCs (System-on-Chips wie Apple Silicon, Qualcomm Snapdragon oder Google Tensor) integrieren spezialisierte Neural Processing Units (NPUs) und mobile Grafikprozessoren (GPUs), die Matrix-Multiplikationen mit einem Bruchteil des Energiebedarfs herkömmlicher Rechenkerne ausführen.

---

## Native On-Device-Laufzeiten im Überblick

Um Sprachmodelle und Einbettungs-Netzwerke direkt auf dem Endgerät auszuführen, nutzen App-Entwickler spezialisierte Laufzeit-Engines:

```
┌─────────────────────────────────────────────────────────────┐
│                 Mobile Applikations-Schicht                 │
│              (Swift / Kotlin / Rust / Web-View)             │
└──────────────────────────────┬──────────────────────────────┘
                               │
         ┌─────────────────────┼─────────────────────┐
         ▼                     ▼                     ▼
┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐
│ Apple CoreML     │  │ PyTorch          │  │ WebLLM / WebGPU  │
│ (iOS / macOS)    │  │ ExecuTorch       │  │ (Cross-Platform) │
│ Nutzt Neural     │  │ Schlanke C++     │  │ Läuft direkt in  │
│ Engine & Metal   │  │ Runtime für AOT  │  │ Tauri & WebViews │
└────────┬─────────┘  └────────┬─────────┘  └────────┬─────────┘
         │                     │                     │
         ▼                     ▼                     ▼
┌─────────────────────────────────────────────────────────────┐
│ Hardware: NPU (Apple ANE / Hexagon) & GPU (Metal / Vulkan)  │
└─────────────────────────────────────────────────────────────┘
```

### 1. Apple CoreML und Metal
Für iOS, iPadOS und macOS stellt CoreML die native Inferenz-Schnittstelle dar. Modelle werden im `.mlpackage`-Format bereitgestellt. CoreML entscheidet zur Laufzeit dynamisch, ob ein Tensor-Layer auf der CPU, der GPU oder der energiesparenden Apple Neural Engine (ANE) berechnet wird. Dies ermöglicht Token-Generierungsraten von 30 bis 60 Tokens pro Sekunde bei minimaler Erwärmung des Geräts.

### 2. PyTorch ExecuTorch
ExecuTorch ist das offizielle, kompakte On-Device-Framework von Meta für PyTorch-Modelle. Es zeichnet sich durch einen extrem geringen Speicher-Footprint (wenige Megabyte Binärgröße) aus und unterstützt Ahead-of-Time-Kompilierung (AOT) für Android (über NNAPI und Qualcomm Hexagon-Delegates) sowie für iOS.

### 3. WebLLM und WebGPU
Für plattformübergreifende Desktop- und Mobil-Apps, die auf Webtechnologien basieren (z. B. mit [Tauri](https://github.com/tauri-apps/tauri)), erlaubt die WebGPU-Schnittstelle die hardwarebeschleunigte Modellausführung direkt im WebView-Kontext. WebLLM lädt quantisierte Gewichte in den GPU-Speicher des Browsers, ohne dass plattformspezifische native Binärdateien kompiliert werden müssen.

---

## Modellkompression und Quantisierung

Ein unkomprimiertes Sprachmodell mit 7 Milliarden Parametern in 16-Bit-Fließkommapräzision (FP16) belegt rund 14 Gigabyte Arbeitsspeicher – eine Größe, die auf Standard-Smartphones sofort zum Absturz durch das Betriebssystem (Out-of-Memory / OOM-Kill) führt.

### Quantisierungsverfahren für Endgeräte:
* **4-Bit-Gewichtsquantisierung (GGUF / AWQ):** Reduziert den Speicherbedarf eines Modells um ca. 70 Prozent (z. B. von 14 GB auf 3,8 GB). Ein 3B-Parameter-Modell belegt in 4-Bit-Quantisierung lediglich etwa 1,8 GB RAM und lässt sich selbst auf Mittelklasse-Smartphones dauerhaft im Speicher halten.
* **Perplexity vs. Effizienz:** Moderne Quantisierungstechniken (wie AWQ oder Q4_K_M) bewahren über 98 Prozent der logischen Leistungsfähigkeit des Basismodells, verringern jedoch den Speicherbandbreitenbedarf drastisch. Da die Inferenzgeschwindigkeit auf Mobilgeräten primär durch die Speicherbandbreite (Memory Bandwidth) limitiert ist, steigert die Quantisierung die Ausgabegeschwindigkeit signifikant.

---

> [!NOTE]
> Wie auf dem Endgerät gespeicherte Dokumente ohne Serveranbindung durchsucht und später synchronisiert werden, zeigt die Unterkategorie [Local-First-Architekturen, Offline-RAG und CRDT-Sync](local-first-offline-rag.md).
