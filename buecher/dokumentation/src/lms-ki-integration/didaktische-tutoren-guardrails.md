# Didaktische Tutoren, sokratischer Dialog und Guardrails

[Übergeordnete Kategorie: Lernmanagement-Systeme und KI-Framework-SDKs](../lms-ki-integration.md)

Im Bildungsbereich besteht das Ziel eines Werkzeugs nicht in der schnellen Erledigung einer Arbeit durch Automatisierung, sondern im Aufbau von Kompetenzen und Verständnis bei den Lernenden. Wenn ein Sprachmodell Schülern oder Studierenden auf Knopfdruck fertige Aufsätze oder mathematische Lösungen liefert, wird der eigentliche Lernprozess untergraben.

---

## Das Prinzip des sokratischen Dialogs

Ein didaktisch integriertes KI-Framework-SDK agiert nicht als Auskunftsautomat, sondern als **sokratischer Tutor**. Es führt Lernende durch gezielte Leitfragen schrittweise zur eigenen Erkenntnis:

```
[Lernender: "Wie lautet die Lösung für Aufgabe 3?"]
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│ 1. Didaktischer Guardrail-Filter                            │
│    Erkennt Aufforderung zur vorzeitigen Lösungsabgabe       │
└────────────────────────┬────────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────────┐
│ 2. Scaffolding-Strategie (Didaktische Stützung)             │
│    Zerlegt die Gesamtaufgabe in den ersten Teilschritt      │
└────────────────────────┬────────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────────┐
│ 3. Sokratische Rückfrage an den Lernenden                   │
│    "Schauen wir uns den ersten Schritt an: Welche Kräfte    │
│     wirken auf den Körper, bevor er sich in Bewegung setzt?"│
└─────────────────────────────────────────────────────────────┘
```

### Kernregeln für sokratische Tutoren:
1. **Keine direkte Lösungsfreigabe:** Der System-Prompt verbietet strikt die vorzeitige Ausgabe vollständiger Rechenwege oder kompletter Texte.
2. **Identifikation von Fehlkonzepten:** Antwortet ein Lernender falsch, analysiert das Modell die Ursache des Missverständnisses (*„Du hast hier Masse mit Gewichtskraft verwechselt. Erinnerst du dich an den Unterschied?“*), anstatt nur die Korrektheit zu verneinen.
3. **Frustrationsbegrenzung:** Droht ein Lernender nach mehreren Fehlversuchen zu resignieren, lockert der Tutor die Hilfestellung schrittweise oder schlägt vor, die Frage für die nächste Präsenzeinheit der Lehrkraft vorzulegen.

---

## Didaktische Schutzplanken (Guardrails) im Code

Damit das Sprachmodell seine didaktische Rolle zuverlässig beibehält, müssen Leitplanken auf mehreren Ebenen implementiert werden:

* **Strikte System-Prompts:** Verankerung pädagogischer Rollenprofile (z. B. Sprachniveau angepasst an Schuljahrgänge, Verzicht auf unnötig akademische Fachbegriffe bei jüngeren Lernenden).
* **Ausgaben-Validierung:** Erkennt ein nachgelagerter Classifier oder ein Guardrail-Framework (wie NeMo Guardrails oder Llama Guard), dass das Modell eine vollständige Prüfungsantwort generiert hat, wird der Stream abgefangen und durch einen didaktischen Impuls ersetzt.
* **Thematische Eingrenzung:** Versucht ein Schüler, den Tutor für fachfremde Themen (z. B. Computerspiele oder private Chats) zweckzuentfremden, führt das System das Gespräch höflich, aber bestimmt zum Thema des Kurses zurück.

---

## Formative Begleitung vs. summative Benotung

In der E-Learning-Didaktik wird streng zwischen formativen und summativen Szenarien unterschieden:

| Kriterium | Formatives Feedback (Lernbegleitung) | Summative Bewertung (Prüfung & Noten) |
| :--- | :--- | :--- |
| **Ziel** | Kompetenzerwerb, Reflexion, Üben | Feststellung und Einstufung von Leistung |
| **KI-Einsatz** | **Hervorragend geeignet:** Sofortiges, detailliertes Feedback zu Textentwürfen, Code oder Rechnungen | **Autonom ungeeignet:** Keine autonome Vergabe von Zeugnis- oder Prüfungsnoten |
| **Fehlerfolgen** | Gering; dient als Denkimpuls im geschützten Raum | Hoch; Noten sind justiziabel und haben rechtliche Tragweite |
| **Rolle des Menschen** | Selbstständiges Lernen mit KI-Hilfe | **Zwingend:** Letztverantwortung und Begutachtung durch Lehrkraft |

Autonome KI-Benotungen bergen das Risiko stochastischer Verzerrungen (Bias), Benachteiligung unkonventioneller Lösungswege und unerkannter Halluzinationen. KI-SDKs können Lehrkräften Korrekturraster oder Entwürfe für Beurteilungen vorschlagen, die Notenvergabe bleibt jedoch zwingend eine hoheitliche Aufgabe qualifizierter Pädagogen.

---

> [!NOTE]
> Wie ein solcher KI-Tutor standardisiert über offene E-Learning-Schnittstellen in Systeme wie Moodle oder Canvas eingebunden wird, beschreibt der Abschnitt [LTI-Standards und sichere Tool-Interoperabilität](lti-standards-interoperabilitaet.md).
