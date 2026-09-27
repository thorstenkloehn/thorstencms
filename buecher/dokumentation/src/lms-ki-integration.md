# Lernmanagement-Systeme und KI-Framework-SDKs

Lernmanagement-Systeme (LMS) steuern Kursstrukturen, Lernaktivitäten, Prüfungen und den individuellen Lernfortschritt in Schulen, Universitäten und Unternehmen. Während klassische Webframeworks und CMS auf Information und Auslieferung fokussieren, verfolgen LMS didaktische und pädagogische Ziele: Sie sollen Lernende motivieren, Missverständnisse aufdecken und den Lernprozess aktiv begleiten.

Die Integration von KI-Framework-SDKs in ein LMS unterscheidet sich grundlegend von gewöhnlichen Wissensassistenten:

* **Sokratische Anleitung statt fertiger Antworten:** Ein KI-Tutor im Bildungsbereich darf Lernenden bei Übungen und Aufgaben nicht einfach die fertige Musterlösung vorsagen. Er muss über didaktische Schutzplanken (Guardrails) angeleitet werden, Verständnisfragen zu stellen, Denkimpulse zu geben und Fehlkonzepte schrittweise aufzudecken.
* **Besonderer Schutz von Lerndaten:** Aufsätze, Testergebnisse und Lernbiografien sind hochsensible personenbezogene Daten (oft von Minderjährigen). Sie dürfen niemals unverschlüsselt oder für Trainingszwecke an externe Modellbetreiber übermittelt werden.
* **Standardbasierte Interoperabilität (LTI):** Statt proprietärer Insellösungen erfolgt die Anbindung moderner KI-Dienste über etablierte E-Learning-Standards wie LTI 1.3 Advantage (Learning Tools Interoperability).

```
┌─────────────────────────────────────────────────────────────┐
│                      Lernende / Kurs-UI                     │
│          (Kursraum, interaktive Übung, Aufgabenabgabe)      │
└──────────────────────────────▲──────────────────────────────┘
                               │ HTTPS / LTI 1.3 (OIDC / JWT)
┌──────────────────────────────▼──────────────────────────────┐
│ LMS-Plattform (Moodle, Canvas LMS, OpenOlat)                │
│  ├─ Kursverwaltung, Einschreibungen & Rollen (Lehrer/Schüler│
│  ├─ Notenbuch (Gradebook) & Leistungsstände                 │
│  └─ LTI-Plattform-Security & Rollen-Mapping                 │
└──────────────────────────────▲──────────────────────────────┘
                               │ LTI Launch / REST-API
┌──────────────────────────────▼──────────────────────────────┐
│ KI-Lernservice (LTI Tool Provider mit KI-SDK)               │
│  ├─ Didaktische Guardrails (Sokratischer Dialog)            │
│  ├─ Pseudonymisierungs-Proxy (Schutz persönlicher Daten)    │
│  └─ Aufgaben- und Feedback-Synthese                         │
└──────────────────────────────▲──────────────────────────────┘
                               │ xAPI-Statements / Relationen
┌──────────────────────────────▼──────────────────────────────┐
│ Persistenz: PostgreSQL (LMS-Daten) & LRS (Lernprotokolle)   │
└─────────────────────────────────────────────────────────────┘
```

---

## Kernaufgaben der LMS-Integration

1. **Didaktische Schutzplanken (Guardrails):** System-Prompts und Workflow-Graphen müssen sicherstellen, dass die KI auf dem Niveau der jeweiligen Lernstufe agiert, Fehlversuche positiv verstärkt und das selbstständige Denken fördert.
2. **Formatives Feedback statt summativen Noten:** KI-SDKs eignen sich hervorragend für formative Rückmeldungen während des Lernens (Übungen, Schreibberatung). Rechtlich bindende Prüfungsnoten (summative Bewertung) dürfen wegen Halluzinationsrisiken und fehlender Justiziabilität nicht autonom von Modellen vergeben werden.
3. **Nahtlose System-Interoperabilität:** Durch LTI 1.3 kann derselbe KI-Tutor-Service in verschiedenen LMS-Instanzen betrieben werden, ohne dass Benutzerkonten oder Passwörter doppelt verwaltet werden müssen.

---

## Unterkategorien dieses Kapitels

Die didaktischen und technischen Integrationsmuster gliedern sich in drei Schwerpunkte:

* [Didaktische Tutoren, sokratischer Dialog und Guardrails](lms-ki-integration/didaktische-tutoren-guardrails.md): Pädagogische Gesprächsführung, Leitfragen statt Lösungen, Erkennung von Fehlkonzepten und Grenzen automatischer Notengebung.
* [LTI-Standards und sichere Tool-Interoperabilität](lms-ki-integration/lti-standards-interoperabilitaet.md): Standardisierte Anbindung externer KI-Dienste über LTI 1.3 Advantage, Rollen-Mapping und Gradebook-Rückmeldung via AGS.
* [Lerndatenschutz, Pseudonymisierung und xAPI-Protokollierung](lms-ki-integration/datenschutz-xapi-analytics.md): Schutz sensibler Leistungsdaten, Pseudonymisierung vor Modellaufrufen und strukturierte Protokollierung von Lernschritten via xAPI.

---

> [!NOTE]
> Geprüfte Open-Source-Plattformen wie Moodle und Canvas werden im Kapitel [Sprachmodelle in Lernmanagement-Systemen](sprachmodelle/lms.md) bewertet. E-Learning-Standards wie SCORM werden unter [Lernmanagement-Systeme](klassische-lms.md) behandelt.
