# Lerndatenschutz, Pseudonymisierung und xAPI-Protokollierung

[Übergeordnete Kategorie: Lernmanagement-Systeme und KI-Framework-SDKs](../lms-ki-integration.md)

Lernbiografien, Aufsatzentwürfe, Fehleranalysen und Reaktionszeiten sind hochsensible personenbezogene Daten. Im Schul- und Hochschulbereich gelten durch DSGVO, europäische Bildungsrichtlinien und internationale Vorgaben (wie FERPA) besonders strenge rechtliche Schutzvorschriften für Lernende. Die unbedachte Weiterleitung von Schülerarbeiten an öffentliche Modell-APIs stellt einen gravierenden Verstoß gegen geltendes Recht dar.

---

## Das Prinzip der minimalen Datenweitergabe (Pseudonymisierung)

Ein externes KI-Framework-SDK benötigt für eine didaktische Hilfestellung weder den Klarnamen, die E-Mail-Adresse noch den Wohnort der Lernenden. Die Architektur muss eine strikte Trennung zwischen Identität und Inferenz gewährleisten:

```
[Lernender: "Anna Schmidt"]
             │
             ▼
┌─────────────────────────────────────────────────────────────┐
│ 1. LMS-Identitätsgrenze (Moodle / Canvas)                   │
│    Ersetzt Identität durch zufällige UUID:                  │
│    `sub: "urn:lti:user:a8f9-4b21-99cd"`                     │
└────────────────────────────┬────────────────────────────────┘
                             │ Pseudonymisierte Session
┌────────────────────────────▼────────────────────────────────┐
│ 2. Eingangs-Filterung (PII-Scrubber / Anonymisierer)        │
│    Entfernt persönliche Daten aus Freitext-Eingaben         │
│    ("Ich heiße Anna..." ──► "Ich heiße [SCHÜLERIN]...")     │
└────────────────────────────┬────────────────────────────────┘
                             │ Anonymisierter Prompt
┌────────────────────────────▼────────────────────────────────┐
│ 3. KI-Framework-SDK / Modell-Inferenz                       │
│    Vertragliche "Zero Data Retention / No Training"-Klausel │
└────────────────────────────┬────────────────────────────────┘
                             │ Didaktische Rückmeldung
┌────────────────────────────▼────────────────────────────────┐
│ 4. Lokale Zuordnung im Browser der Lernenden                │
│    (Personenbezogene Verknüpfung erfolgt erst auf dem Client│
└─────────────────────────────────────────────────────────────┘
```

### Technische Schutzmaßnahmen:
1. **Pseudonyme LTI-Identifier:** Über LTI 1.3 wird ausschließlich ein kryptografischer Benutzer-Hash (`sub`) übertragen. Das KI-System speichert keine realen Personenbezüge.
2. **PII-Scrubbing im Freitext:** Da Lernende in dialogischen Eingaben oft unbedacht persönliche Details erwähnen (*„Mein Name ist Anna aus der 8b...“*), fängt eine lokale NLP-Vorstufe personenbezogene Entitäten (Namen, Telefonnummern, Schulnamen) ab und ersetzt sie durch generische Platzhalter.
3. **Verbot des Modelltrainings (Zero Data Retention):** Schul- und Universitätsbetreiber dürfen KI-Modelle nur über kommerzielle Enterprise-Schnittstellen oder On-Premise-Modelle (z. B. via Ollama oder vLLM) anbinden, die vertraglich garantieren, dass Daten nach der Inferenz sofort gelöscht und keinesfalls für das Training zukünftiger Modellgenerationen verwendet werden.

---

## Lernstandsanalysen über xAPI und Learning Record Stores (LRS)

Um den Lernerfolg transparent zu machen, ohne die Privatsphäre zu gefährden, werden Interaktionen mit dem KI-Tutor standardisiert über die **Experience API (xAPI)** protokolliert:

### xAPI-Aussagen (Statements):
Interaktionen werden im standardisierten Triple-Format `Akteur -> Verb -> Objekt` mit didaktischem Kontext abgebildet:

```json
{
  "actor": { "account": { "name": "urn:lti:user:a8f9-4b21", "homePage": "https://lms.schule.de" } },
  "verb": { "id": "http://adlnet.gov/expapi/verbs/asked", "display": { "de-DE": "fragte nach Hinweis" } },
  "object": { "id": "https://kurs.schule.de/physik/aufgabe-4", "definition": { "name": { "de-DE": "Kräftezerlegung" } } },
  "result": { "extensions": { "https://schema.org/hintCount": 2, "https://schema.org/misconception": "Masse/Gewichtskraft" } }
}
```

### Didaktischer Mehrwert aggregierter LRS-Daten:
* **Aggregierte Lehrkraft-Übersicht:** Lehrpersonen sehen im LMS-Dashboard, bei welchen Aufgaben 80 % der Klasse nach Hinweisen fragten oder an welchem Schritt typische Fehlkonzepte auftraten.
* **Keine Überwachung:** Durch die Aggregation im Learning Record Store (LRS) lassen sich Curricula und Übungsblätter datengestützt verbessern, ohne dass Lehrkräfte private Schüler-Chatverläufe manuell ausspähen müssen.

---

> [!NOTE]
> Die allgemeinen rechtlichen Datenschutzgrundsätze dieses Buchprojekts sind unter [Datenschutz](../Datenschutz.md) dokumentiert.
