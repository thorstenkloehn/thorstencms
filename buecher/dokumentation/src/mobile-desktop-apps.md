# Mobile und Desktop-Apps in Content- und Wissenssystemen

Webanwendungen bieten universelle Erreichbarkeit über den Browser. Für viele Aufgaben in
Content-Management-Systemen (CMS), Lernplattformen (LMS), Wissenssystemen und Entwicklungs-Workflows
stoßen reine Browser-Tabs jedoch an Grenzen: Offline-Nutzung, Dateisystem-Integration,
Hardware-Zugriff (Kamera, Biometrie), Push-Benachrichtigungen und flüssige Interaktion
erfordern spezialisierte **Mobile- und Desktop-Applikationen**.

Dieses Kapitel beschreibt, wie native, hybride und plattformübergreifende Clients
architektonisch mit den Kernsystemen dieses Buches verzahnt werden.

---

## Architekturmatrix: Clients über alle Systemklassen

Die Rolle von mobilen Begleit-Apps und Desktop-Programmen unterscheidet sich je nach Systemklasse fundamental:

| Dimension | CMS | LMS | Wissenssysteme | Webframeworks & APIs |
| :--- | :--- | :--- | :--- | :--- |
| **Primäre Aufgabe** | Mobiles Erfassen, Redaktions-Reviews & Medien-Upload | Mobiles Offline-Lernen & Fristen-Monitoring | Lokale Notiz- & Graph-Verwaltung | Client-Anbindung, Auth & Zustandsabgleich |
| **Architekturmodell** | Online-First (Headless API) | Hybrid (selektives Offline-Caching) | Local-First (Daten primär lokal) | Backend-for-Frontend (BFF) & REST/GraphQL |
| **Client-Speicher** | Temporärer Cache / SQLite | SQLite & verschlüsselte SCORM-Container | Lokale Markdown-Dateien oder SQLite | Zustandsspeicher (State Stores) & SQLite |
| **Server-Speicher** | PostgreSQL oder Inhaltsdateien | PostgreSQL | Optionaler Sync-Server (PostgreSQL/S3) | PostgreSQL (relationale Source of Truth) |
| **Schlüsselfunktion** | Kamera-Upload, Push-Freigaben | Offline-Player, Lernzeit-Tracking | Schnelle Suche, volle Datenhoheit | Biometrische Auth (PKCE), Push, WebSockets |

---

## Unterkategorien: gefilterte Softwareauswahl

- [Local-First PKM- und Wissens-Apps](apps/pkm-notizen.md)
- [Mobile Bildungs- und E-Learning-Apps](apps/lms-mobile.md)
- [Redaktions- und Content-Clients](apps/cms-clients.md)
- [Cross-Platform-App-Frameworks](apps/cross-platform-frameworks.md)
- [Local-First- und Synchronisations-Engines](apps/offline-sync.md)

---

## 1. Mobile & Desktop in Content-Management-Systemen (CMS)


In redaktionellen Umgebungen ergänzen Apps den Desktop-Webbrowser gezielt um mobile Arbeitsabläufe:

- **Redaktion von unterwegs:** Schnelles Verfassen von Entwürfen, Korrekturlesen und Auslösen von Veröffentlichungs-Workflows (Publishing) über Mobilgeräte.
- **Medien-Upload vor Ort:** Reporter und Redakteure können Fotos und Videos direkt über die Smartphone-Kamera aufnehmen, serverseitig über das CMS komprimieren lassen und in die Medienbibliothek einpflegen.
- **Push-Benachrichtigungen für Freigaben:** Redaktionsleiter erhalten unmittelbare Benachrichtigungen, wenn ein Entwurf zur redaktionellen Abnahme bereitsteht.
- **Headless-Anbindung:** Moderne CMS (wie Strapi, Directus oder Drupal) liefern strukturierte Inhalte über REST- oder GraphQL-Endpunkte aus. Mobile Apps fungieren dabei als reine Präsentations- und Eingabeclients ohne eigene CMS-Geschäftslogik.
- Weiterführende Aspekte zur Entkopplung von Inhalten finden sich im Kapitel [Headless und Decoupled CMS](cms/headless.md).

---

## 2. Mobile & Desktop in Lernmanagement-Systemen (LMS)

Für E-Learning und Bildungssysteme sind mobile Clients der Schlüssel zu unterbrechungsfreiem Lernen:

- **Offline-First für Lerninhalte:** Pendler oder Lernende ohne permanente Breitbandverbindung laden Kurspakete, Videos und interaktive Module (SCORM/H5P) vorab auf das Endgerät herunter.
- **Laufzeit-Tracking & Synchronisation:** Quiz-Ergebnisse, Bearbeitungszeiten und Lernfortschritte werden lokal in einer verschlüsselten Client-Datenbank erfasst. Sobald eine Netzwerkverbindung besteht, synchronisiert die App die Daten mit der zentralen PostgreSQL-Datenbank des LMS.
- **Termine und Fristenüberwachung:** Push-Nachrichten erinnern an bevorstehende Abgabetermine, Live-Seminare oder auslaufende Zertifizierungsfristen (siehe [Compliance, Pflichtschulungen und Talent-Suiten](lms/compliance-enterprise.md)).
- **Praxisbeispiele:** Die offizielle *Moodle App* und *Canvas Student* demonstrieren diese hybride Architektur; Systeme wie *Kolibri* treiben diesen Ansatz bis zum vollständigen dateibasierten Offline-Betrieb (siehe [Mobile Learning und ILT-Präsenzseminare](lms/mobile-blended.md)).

---

## 3. Mobile & Desktop in Wissenssystemen: Das Local-First-Paradigma

Im Bereich des persönlichen Wissensmanagements (PKM) und vernetzter Notizen dominiert das **Local-First-Prinzip**:

- **Datenhoheit auf dem Endgerät:** Die Daten liegen primär als unverschlüsselte Textdateien (Markdown, Org-Mode) oder in lokalen SQLite-Datenbanken direkt auf der Festplatte des Nutzers.
- **Latenzfreie Interaktion:** Tastaturkürzel, Volltextindizierung und Graph-Visualisierungen reagieren ohne Netzwerkverzögerung in Millisekunden.
- **Konfliktfreie Synchronisation (CRDTs):** Werden Notizen auf Laptop und Smartphone gleichzeitig geändert, lösen Algorithmen wie CRDTs (Conflict-free Replicated Data Types) oder git-basierte Merges Konflikte mathematisch auf, ohne Datenverlust zu riskieren.
- **Offene Desktop- und Mobilvertreter:** Werkzeuge wie *Joplin*, *SiYuan* oder *Logseq* verdeutlichen den Übergang von serverseitigen Wikis zu dezentralen Wissens-Apps (siehe [Visuelle, Local-First und agentische Systeme](wissenssysteme/local-first.md)).

---

## 4. Technische Grundlagen und Webframeworks

Die Anbindung von Mobile- und Desktop-Clients stellt spezifische Anforderungen an die Backend- und Frontend-Architektur:

### Client-Technologie-Stacks

Moderne Cross-Platform-Technologien ermöglichen die Wiederverwendung von Webtechnologien auf mobilen und Desktop-Betriebssystemen:

| Technologie | Plattformen | Architektur | Stärken & Einsatzzweck |
| :--- | :--- | :--- | :--- |
| **Progressive Web App (PWA)** | Web, Android, Desktop | Browser-Sandbox + Service Worker | Keine App-Store-Pflicht, einfache Installation, Offline-Caching via Cache Storage |
| **Capacitor** | iOS, Android, Desktop | Web-View + nativer Plugin-Bridge | Verwandelt bestehende Single-Page-Applications (React, Vue) in native Apps |
| **React Native** | iOS, Android | Native UI-Komponenten via JavaScript-Bridge | Nahezu native Performance mit einheitlicher Web-Entwicklererfahrung |
| **Flutter** | iOS, Android, Desktop | Eigene Render-Engine (Skia/Impeller) in Dart | Pixelgenaue Konsistenz über alle Betriebssysteme hinweg |
| **Tauri** | Windows, macOS, Linux | Web-Frontend + leichtgewichtiger Rust-Kern | Extrem schlanke Desktop-Apps mit minimalem Speicherverbrauch (Alternative zu Electron) |

### Backend-Architektur: Authentifizierung & APIs

- **Authentifizierung ohne Secrets:** Mobile und Desktop-Apps können keine geheimen Client-Schlüssel sicher speichern (Public Clients). Die Authentifizierung erfolgt standardmäßig über **OAuth 2.0 mit PKCE** (Proof Key for Code Exchange).
- **Backend-for-Frontend (BFF):** Um Latenzen und Datenvolumen im Mobilfunknetz zu minimieren, aggregiert ein BFF-Endpunkt Daten aus mehreren relationalen Tabellen in eine einzige kompakte JSON-Antwort.
- **Echtzeit-Synchronisation:** WebSockets oder Server-Sent Events (SSE) übertragen Aktualisierungen sofort an aktive Clients, während Push-Dienste (APNs für Apple, FCM für Google) inaktive Apps aufwecken.

---

## 5. Querschnittsanforderungen: Persistenz und Konsistenz

Die Integration von Apps in die Gesamtdatenhaltung des Buches folgt klaren Regeln:

1. **Relationale Source of Truth:**
   Auf Serverebene bleibt **PostgreSQL** die verbindliche Hauptdatenbank für alle Benutzer-, Kurs-, Inhalts- und Revisionsdaten. Mobile Clients sind Replikat- oder Konsumenten-Knoten, keine alternativen Datensilos.

2. **Robuste Offline-Speicherung:**
   Für lokale Caches und Offline-Zustände auf Mobilgeräten ist **SQLite** der dokumentierte Standard. Bei dateibasierten Wissenssystemen fungiert das lokale Dateisystem als Träger.

3. **Konfliktbehandlung:**
   Schreibzugriffe von mehreren Endgeräten erfordern klare Strategien: Entweder serverseitiges Optimistic Locking (mit Zeitstempeln und Revisionsnummern) oder automatisierte CRDT-Merges bei kollaborativen Dokumenten.

---

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: 26. September 2026. Redaktionelle Auswahl nach der
[gemeinsamen Bewertungsmethode](software.md). Die Reihenfolge priorisiert
Reife und anschließend die Eignung für diese Kategorie.

| Rang | Software | Lizenz des Kerns | Reifegrad | Schwerpunkt | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Joplin](https://github.com/laurent22/joplin) | AGPL-3.0 | Sehr hoch | Multi-Plattform Desktop- und Mobile-Notizverwaltung | Dateien: [Markdown-Dateien mit E2EE und SQLite/PostgreSQL-Sync](https://joplinapp.org/) |
| 2 | [SiYuan](https://github.com/siyuan-note/siyuan) | AGPL-3.0 | Sehr hoch | Block-basierter persönlicher Wissensgraph (Desktop & Mobile) | Dateien: [Lokales JSON-Dateisystem im Arbeitsbereich](https://github.com/siyuan-note/siyuan/blob/master/docs/WORKSPACE.md) |
| 3 | [Moodle App](https://github.com/moodlehq/moodleapp) | GPL-3.0-or-later | Sehr hoch | Mobile Lern- und Kurs-App mit Offline-Synchronisation | PostgreSQL: [Moodle-Backend mit PostgreSQL-Persistenz](https://docs.moodle.org/all/de/PostgreSQL) |
| 4 | [Tauri](https://github.com/tauri-apps/tauri) | Apache-2.0 | Sehr hoch | Leichtgewichtige Multi-Plattform-Laufzeit für Desktop und Mobile | Dateien: [Lokaler Dateisystem- und SQLite-Zugriff](https://tauri.app/) |
| 5 | [Kolibri](https://github.com/learningequality/kolibri) | MIT | Hoch | Plattformübergreifende Offline-App für Bildungsinhalte | Dateien: [Lokale Inhaltskanäle und Datenbankpakete](https://github.com/learningequality/kolibri) |

### 1. Joplin

**Begründung:** Langjährig etablierte plattformübergreifende Notiz- und Wissensanwendung für Desktop (Windows, macOS, Linux) und Mobile (Android, iOS) mit Ende-zu-Ende-Verschlüsselung und flexiblen Sync-Backends.

**Einordnung:** Konzipiert für persönliche Wissenssammlung und strukturierte Notizen; kein kollaboratives Redaktionssystem für Teams.

Offizielle Grundlage: [Joplin](https://github.com/laurent22/joplin).

### 2. SiYuan

**Begründung:** Moderner Local-First-Editor mit nativer Desktop- und Mobile-Unterstützung; speichert hierarchische Wissensgraphen und Dokumente transparent als JSON-Dateien im lokalen Workspace.

**Einordnung:** Eignet sich primär für persönliches Wissensmanagement (PKM); erfordert für webbasierte Massenpublikation zusätzliche Build-Pipelines.

Offizielle Grundlage: [SiYuan](https://github.com/siyuan-note/siyuan).

### 3. Moodle App

**Begründung:** Weltweit erprobter Open-Source-Client (Capacitor/Ionic) für mobile Bildungs- und Kursnutzung; ermöglicht vollständigen Offline-Download von Lerninhalten und asynchrone Notensynchronisation.

**Einordnung:** Spezifischer Client für Moodle-Plattformen; setzt eine konfigurierte Server-Instanz mit aktivierten Webdiensten voraus.

Offizielle Grundlage: [Moodle App](https://github.com/moodlehq/moodleapp).

### 4. Tauri

**Begründung:** Sicherheitsorientiertes, hochgradig ressourcensparendes Framework zur Erstellung nativer Desktop- und Mobile-Apps mit Web-Frontends und Rust-Backend.

**Einordnung:** Anwendungs-Framework und Laufzeitumgebung; setzt die Eigenentwicklung der fachlichen Benutzeroberfläche und Datenlogik voraus.

Offizielle Grundlage: [Tauri](https://github.com/tauri-apps/tauri).

### 5. Kolibri

**Begründung:** Multi-Plattform-Applikation (Windows, macOS, Linux, Android) von Learning Equality für Offline-Lernszenarien und Schulen ohne Breitbandanbindung; Inhaltskanäle werden dateibasiert synchronisiert.

**Einordnung:** Spezialisiert auf dezentrale Offline-Schulungen; deckt keine universitäre Online-Prüfungsverwaltung ab.

Offizielle Grundlage: [Kolibri](https://github.com/learningequality/kolibri).

---

## Verwandte Kapitel


- [Evolution klassischer Lernmanagement-Systeme](klassische-lms.md): Grundlagen und Kursverwaltung.
- [Mobile Learning und ILT-Präsenzseminare](lms/mobile-blended.md): 5 geprüfte Lösungen für mobiles und hybrides Lernen.
- [Headless und Decoupled CMS](cms/headless.md): Entkoppelte Inhaltsauslieferung für App-Clients.
- [Visuelle, Local-First und agentische Systeme](wissenssysteme/local-first.md): Dezentrale Wissensgraphen und lokale Datenhaltung.
- [Single-Page-Applications](webframeworks/spa.md): Browser-Clients und REST-Schnittstellen.
- [Architekturen im Zusammenhang](architekturen.md): Das Gesamtzusammenspiel der Systemperspektiven.
