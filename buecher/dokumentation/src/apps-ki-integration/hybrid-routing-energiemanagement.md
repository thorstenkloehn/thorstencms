# Hybrid-Routing, Modellkaskadierung und Energiemanagement

[Übergeordnete Kategorie: Mobile und Desktop-Apps und KI-Framework-SDKs](../apps-ki-integration.md)

Auf Mobilgeräten und Laptops ist Rechenleistung keine unbegrenzt verfügbare Ressource. Kontinuierliche Modellausführung auf der NPU oder GPU führt unweigerlich zu zwei gravierenden Problemen: raschem Batterieverbrauch und thermischer Drosselung (Thermal Throttling), bei der das Betriebssystem die Taktrate der Prozessoren drastisch senkt, um Hardwareschäden zu verhindern.

---

## Das asymmetrische Modell-Kaskadierungs-Muster

Um eine optimale Balance zwischen Reaktionsschnelligkeit, Antwortqualität und Energieverbrauch zu erzielen, setzen moderne Applikationen auf ein **zweistufiges Hybrid-Routing**:

```
[Benutzeraktion in der mobilen App]
                 │
                 ▼
┌─────────────────────────────────────────────────────────────┐
│ Stufe 1: Lokale Edge-Triage (Kompaktmodell: 1B–3B Parameter)│
│  ├─ Sofortige Beantwortung einfacher Fragen (Offline)       │
│  ├─ In-Line-Autovervollständigung (Ghost-Text)              │
│  └─ Absichtserkennung (Intent Classification & Routing)     │
└────────────────────────────┬────────────────────────────────┘
                             │
             ┌───────────────┴───────────────┐
             │ Frage lokal lösbar?           │
             ▼                               ▼
    [Ja: Sofort anzeigen]           [Nein: Hohe Komplexität / Web-RAG]
                                             │
                             ┌───────────────┴───────────────┐
                             │ Umwelt-Check auf dem Endgerät │
                             │  ├─ Internetverbindung aktiv? │
                             │  └─ Akkustand > 15 %?         │
                             └───────────────┬───────────────┘
                                             │
                                             ▼
                             ┌───────────────────────────────┐
                             │ Stufe 2: Cloud-Inferenz       │
                             │ (Zentrales Gateway / LiteLLM) │
                             └───────────────────────────────┘
```

### 1. Stufe 1 (Lokales Kompaktmodell)
Ein kleines, auf dem Gerät vorgehaltenes 1B- bis 3B-Modell (z. B. Gemma 2B oder Qwen 2.5) agiert als lokaler Filter und Triage-Instanz. Es beantwortet einfache Formatierungs- und Klassifizierungsfragen in Millisekunden und erkennt, ob für eine fundierte Antwort externe Bibliotheken oder komplexe Argumentationsketten erforderlich sind.

### 2. Stufe 2 (Cloud-Delegation)
Nur wenn die Aufgabe die Wissens- oder Rechengrenzen des lokalen Modells übersteigt, leitet das KI-Framework-SDK die Anfrage an das zentrale Backend (z. B. über ein [LiteLLM](../sprachmodelle/bibliotheken.md)-Gateway) weiter.

---

## Kontext- und akkugesteuertes Ressourcenmanagement

Mobile Betriebssysteme (iOS und Android) überwachen den Energieverbrauch von Hintergrundprozessen streng. Eine App, die unkontrolliert Inferenz-Tasks im Hintergrund ausführt, wird vom Betriebssystem zwangsweise beendet (Background Execution Kill).

### Schutzregeln für die App-Architektur:
* **Akkustand-Wächter (Battery Guard):** Fällt die verbleibende Akkuladung unter einen Schwellenwert (z. B. 20 Prozent) oder befindet sich das Gerät im Energiesparmodus des Betriebssystems, pausiert die App lokale Vektorisierungs-Pipelines für neue Dokumente und schaltet auf leichtgewichtige Cloud-Aufrufe um.
* **Thermal Throttling Prävention:** Die App überwacht die thermischen Status-APIs des Betriebssystems (wie `ProcessInfo.thermalState` unter iOS). Meldet das System erhöhte Temperaturwerte, erzwingt das KI-SDK Ruhepausen zwischen aufeinanderfolgenden Token-Generierungen.
* **Intelligenter lokaler Semantik-Cache:** Identische oder hochgradig ähnliche Anfragen werden in einer lokalen Tabelle in `sqlite-vec` gecacht. Liefert die Kosinus-Ähnlichkeit zu einer früheren Frage einen Wert nahe 1.0, wird die gespeicherte Antwort unmittelbar ausgegeben, ohne dass NPU oder Cloud erneut beansprucht werden.

---

> [!NOTE]
> Die serverseitige Verarbeitung und Weiterleitung solcher Cloud-Anfragen wird im Kapitel [Webframeworks und KI-Framework-SDKs](web-ki-integration.md) detailliert beschrieben.
