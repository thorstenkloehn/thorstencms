# LTI-Standards und sichere Tool-Interoperabilität

[Übergeordnete Kategorie: Lernmanagement-Systeme und KI-Framework-SDKs](../lms-ki-integration.md)

Bildungseinrichtungen betreiben heterogene Plattformlandschaften: Universitäten nutzen Canvas LMS oder Moodle, Schulen oft OpenOlat oder lokale Lernportale. Anstatt für jedes System ein proprietäres Plugin zu entwickeln, setzt die moderne Bildungsarchitektur auf den offenen Interoperabilitätsstandard **LTI 1.3 Advantage** (Learning Tools Interoperability) der 1EdTech-Allianz.

---

## Das LTI-Architekturmodell für KI-Dienste

Über LTI wird ein mit einem KI-Framework-SDK entwickelter Lerndienst als eigenständiger **Tool Provider** betrieben und nahtlos in das LMS als **Plattform** eingebettet:

```
[LMS-Plattform: Moodle / Canvas]
             │
             │ 1. OIDC Launch Request (Initiierung)
             ▼
┌─────────────────────────────────────────────────────────────┐
│ 2. Authentifizierung & JWT-Signatur (OAuth 2.0 / JWKS)       │
│    LMS signiert Token mit privatem RSA-Schlüssel            │
└────────────────────────────┬────────────────────────────────┘
                             │
                             │ 3. Weiterleitung mit id_token
                             ▼
┌─────────────────────────────────────────────────────────────┐
│ KI-Tutor-Service (LTI Tool Provider)                        │
│  ├─ Validiert JWT über öffentlichen LMS-Schlüssel (JWKS)    │
│  ├─ Erkennt Rolle (Instructor vs. Learner via NRPS)         │
│  └─ Startet didaktische KI-Session im iFrame                │
└────────────────────────────┬────────────────────────────────┘
                             │
                             │ 4. Rückmeldung via LTI AGS
                             ▼
[LMS-Notenbuch: Speichert Übungsfortschritt & Feedback]
```

### Der sichere Verbindungsaufbau:
1. **OpenID Connect (OIDC) Launch:** Klickt ein Schüler im LMS auf eine KI-Lernaktivität, stößt das LMS einen standardisierten OIDC-Handshake an.
2. **Kryptografische Signatur mit JWT:** Das LMS übermittelt ein signiertes JSON Web Token (JWT), das Kontext-IDs (Kurs-ID, Aufgaben-ID) und Benutzer-Rollen enthält. Der KI-Dienst prüft die Signatur über den öffentlichen Schlüsselsatz (JWKS) des LMS.
3. **Nahtloses Single Sign-On (SSO):** Lernende müssen kein gesondertes Konto anlegen und kein zusätzliches Passwort eingeben.

---

## Die Kern-Dienste von LTI 1.3 Advantage

Der Standard umfasst drei Erweiterungsdienste, die für KI-gestützte Lernwerkzeuge essenziell sind:

### 1. Names and Role Provisioning Service (NRPS)
Ermöglicht dem KI-Dienst die sichere Abfrage von Kursrollen und Teilnehmerlisten.
* **Differenzierte Modi:** Erkennt das KI-Tool die Rolle `Instructor` (Lehrkraft), schaltet es in den **Autoren-Modus** (Generierung von Übungsfragen, Erstellung von Rubriken, Musterlösungs-Design).
* Bei der Rolle `Learner` schaltet das Tool automatisch in den geschützten **sokratischen Tutor-Modus**.

### 2. Assignment and Grade Services (AGS)
Ermöglicht dem KI-Lernservice das strukturierte Zurückschreiben von Ergebnissen in das Gradebook des LMS:
* Nach Abschluss einer interaktiven Übung übermittelt der KI-Dienst erreichte Punktzahlen, Bearbeitungszeiten und didaktische Feedback-Texte über die LTI-AGS-Schnittstelle an das LMS.
* Die Lehrkraft behält im Notenbuch die volle Übersicht über alle Schüleraktivitäten.

### 3. Deep Linking
Lehrkräfte können beim Anlegen eines Kurses direkt aus dem LMS heraus den KI-Dienst aufrufen, dort spezifische Übungsmodule oder Themenbereiche konfigurieren und diese mit einem Klick als fertige Aktivität in den Kursplan einbinden.

---

> [!NOTE]
> Welche Vorgaben zum Schutz der Privatsphäre von Schülerinnen und Schülern bei der Token-Übertragung gelten, vertieft die Unterkategorie [Lerndatenschutz, Pseudonymisierung und xAPI-Protokollierung](datenschutz-xapi-analytics.md).
