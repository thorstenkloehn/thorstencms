# Evolution und Architekturen digitaler klassischer LMS

Klassische, monolithische Lernmanagement-Systeme (LMS) bilden die **Generation 1** in der
Evolution digitaler Bildungs- und E-Learning-Plattformen. Diese Architekturlinie reicht von den
frühen Mainframe-Pionieren computergestützten Lernens (CBT) über vernetzte Web-LMS der SCORM-Ära
und Enterprise-Talent-Suiten bis hin zu modernen Standardisierungs- und Compliance-Bausteinen.

LMS stehen an der Schnittstelle zwischen Wissenssystemen und Content-Management: Während Wikis
und Wissensgraphen freie Vernetzung fördern, organisieren LMS Lernprozesse nach festen Rollen,
didaktischen Pfaden, Berechtigungen und nachvollziehbaren Fortschritten.

---

## Architekturmerkmale der klassischen Generation

Drei architektonische Prinzipien einen die klassische LMS-Generation:

1. **Zentrale Kurs- und Nutzerdatenbank:** Ein relationales Kernmodell verwaltet Benutzerkonten, Rollen (Dozenten, Lernende, Administratoren), Kursbelegungen und Noten.
2. **Paketierte Lerninhalte:** Inhalte werden nicht lose verlinkt, sondern als standardisierte Pakete (ZIP-Archive mit Manifestdateien nach AICC oder SCORM) importiert und im LMS entpackt oder ausgeliefert.
3. **Lineares Tracking:** Der Lernfortschritt wird prozessual erfasst (Bearbeitungsstatus, Quiz-Ergebnisse, Verweildauer, Bestehenskriterien).

---

## Die sechs Entwicklungsstufen klassischer LMS

Die Evolution der klassischen Linie lässt sich in sechs Phasen gliedern, die sich historisch
und technisch überlappen:

| Stufe / Phase | Zeitraum | Schwerpunkt & Architektur | Typische Vertreter |
| --- | --- | --- | --- |
| **1. CBT & frühe Web-LMS** | 1960 – 2005 | Mainframe-Terminals, erste Webanwendungen (Perl/PHP), monolithische Kursräume | PLATO, TICCIT, Blackboard Learn, WebCT, [Moodle](https://github.com/moodle/moodle) |
| **2. SCORM-Standardisierung** | 1999 – 2004 | Interoperable Inhaltspakete, Standardisierung der Laufzeitkommunikation (CBT -> LMS) | AICC, SCORM 1.2, SCORM 2004 |
| **3. Open-Source-Reife** | 2002 – 2010 | Community-getragene Erweiterbarkeit, modulare Plugin-Architekturen, Hochschul-Konsortien | Moodle-Plugin-Ökosystem, Sakai |
| **4. Compliance & HR-Tiefe** | 2005 – 2012 | Zertifizierungspflichten, Revisionssicherheit, Verzahnung mit HR- und Talentmanagement | Cornerstone OnDemand, SAP SuccessFactors Learning, Saba |
| **5. Mobile & Blended Learning** | 2010 – 2015 | Companion-Apps (Offline-Synchronisation), Integration von Präsenztraining (ILT) und Raumplanung | Moodle Mobile, Enterprise-ILT-Module |
| **6. Marktkonsolidierung** | 2015 – 2020 | Fusionen großer Suiten, Wachstumsdruck durch Cloud-native Herausforderer | Cornerstone übernimmt Saba, Blackboard-Konsolidierung |

## Unterkategorien: gefilterte Softwareauswahl

- [CBT-Pioniere und frühe Web-LMS](lms/cbt-web-lms.md)
- [SCORM- und Interoperabilitätsstandards](lms/scorm-standards.md)
- [Open-Source-LMS und Konsortialplattformen](lms/open-source.md)
- [Compliance, Pflichtschulungen und Talent-Suiten](lms/compliance-enterprise.md)
- [Mobile Learning und ILT-Präsenzseminare](lms/mobile-blended.md)
- [Cloud-native LMS und LXP-Systeme](lms/cloud-lxp.md)

---


## Detaillierte Chronologie und Generationen

### Generation 1: CBT-Pioniere, Web-LMS & Enterprise-Talent-Suiten (1960 – 2015)

- **1a. CBT-Pioniere (1960 – 1990):** Systeme wie *PLATO* (University of Illinois, 1960) oder *TICCIT* etablierten frühe interaktive Bildschirmlehrgänge auf Großrechnern und dedizierten Terminals. Sie bewiesen die Machbarkeit computerunterstützten Unterrichts lange vor dem World Wide Web.
- **1b. Vernetzte Web-LMS (1990 – 2005):** Mit der Verbreitung des Webs entstanden campusweite Plattformen wie *WebCT* (1996), *Blackboard Learn* (1997) und das quelloffene *Moodle* (2002). Der Schwerpunkt lag auf der Digitalisierung von Hochschulseminaren: Datei-Uploads, Foren, Aufgabenabgaben und strukturierte Wochenpläne.
- **1c. Enterprise-Talent-Suiten (2000 – 2015):** Im Unternehmenssektor wuchsen Systeme wie *Cornerstone OnDemand*, *SAP SuccessFactors* und *Saba* heran, die Schulung nicht akademisch, sondern als Mitarbeiterentwicklung und Leistungsbeurteilung begriffen.

### Generation 2: SCORM-Standardisierung (1999 – 2004)

Vor einheitlichen Standards waren Lerninhalte an das jeweilige Autorensystem oder LMS gebunden. Die Standardisierung löste Inhalte von der Auslieferungsplattform:

- **AICC (1988/1993):** Ursprünglich vom Aviation Industry CBT Committee entwickelt; erster herstellerübergreifender Standard für den Datenaustausch via HTTP.
- **SCORM 1.2 (2001):** Das *Sharable Content Object Reference Model* (ADL) definierte ein standardisiertes XML-Manifest (`imsmanifest.xml`) und ein JavaScript-API zur Übermittlung von Lernstatus (`cmi.core.lesson_status`) und Score an das LMS. Es wurde zum dominierenden Industriestandard.
- **SCORM 2004 (1st bis 4th Edition):** Ergänzte Sequenzierungs- und Navigationsregeln (*Sequencing & Navigation*), um verzweigte Lernpfade abhängig von Testergebnissen zu ermöglichen.

### Generation 3: Open-Source-Ökosysteme (2002 – 2010)

Mit der Reife von [Moodle](https://github.com/moodle/moodle) und Konsortialplattformen wie *Sakai* (2004) zeigte sich die Stärke modularer Architekturen:
- Communitys schufen Tausende Plugins für Bewertungsmethoden, Fragetypen, Anti-Plagiat-Schnittstellen und Videokonferenzen.
- Bildungseinrichtungen erhielten volle Datenhoheit und Anpassbarkeit ohne Lizenzgebühren, trugen jedoch die Betriebs- und Upgrade-Verantwortung selbst.

### Generation 4: Compliance- & Zertifizierungs-Tiefe (2005 – 2012)

In regulierten Branchen (Pharma, Finanzen, Luftfahrt, Medizin) wandelten sich LMS von pädagogischen Werkzeugen zu prüfungsrelevanten Compliance-Systemen:
- Elektronische Signaturen (z. B. nach FDA 21 CFR Part 11).
- Automatische Rezertifizierungszyklen und lückenlose Audit-Trails für behördliche Nachweise.

### Generation 5: Mobile- & Blended-Learning (2010 – 2015)

Monolithische Web-LMS öffneten sich für hybride Lernformate:
- **Mobile-Companion-Apps:** Lernende konnten Kursmodule auf Smartphones herunterladen, offline bearbeiten und bei Netzverbindung synchronisieren.
- **Instructor-Led Training (ILT):** Verwaltung physischer Seminarpräsenzen, Raumressourcen, Dozentenkalender und Anwesenheitslisten innerhalb desselben Datenmodells.

### Generation 6: Fusionen und Übergang zu Cloud-LMS (2015 – 2020)

Der Markt klassischer On-Premise-LMS konsolidierte sich massiv (z. B. Übernahme von Saba durch Cornerstone 2020). Gleichzeitig markiert diese Phase den architektonischen Übergang zur **Generation 2 der übergeordneten LMS-Evolution**: Moderne Cloud-native Architekturen (wie *Canvas LMS*) und dezentrale Learning Experience Platforms (LXP) lösten monolithische Installationen zunehmend ab.

---

## Klassifikationskriterien für LMS-Architekturen

Klassische LMS lassen sich über drei Dimensionen strukturieren:

1. **Content-Interoperabilität:**
   - *Proprietär:* Feste Bindung an proprietäre Formate (historische CBT-Systeme).
   - *SCORM-kompatibel:* Auslieferung interoperabler Zip-Pakete (SCORM 1.2 / 2004).
   - *Moderne Standards:* xAPI (Tin Can API), cmi5 und LTI (Learning Tools Interoperability).

2. **Betriebs- und Lizenzmodell:**
   - *Kommerziell / Enterprise:* Proprietäre SaaS- oder On-Premise-Lizenzen mit HRIS-Kopplung.
   - *Self-hosted Open Source:* Eigenbetriebene Instanzen mit Community-Support und voller Quellcode-Kontrolle.

3. **Fachlicher Einsatzzweck:**
   - *Akademisch (K-12 & Hochschule):* Notenbücher, kollaborative Gruppenarbeit, Semesterstrukturen.
   - *Corporate / Enterprise:* Pflichtschulungen, Skill-Matrizen, Zertifikate und Nachfolgeplanung.

---

## Datenhaltung und der PostgreSQL-Bezug

Gemäß dem [verbindlichen Speicherfilter](software.md#verbindlicher-speicherfilter) dieses Buches
bleiben für Softwareauswahlen nur Lösungen mit dokumentierter **PostgreSQL-** oder **Dateispeicherung** erhalten.

In der klassischen Open-Source-LMS-Landschaft war der Großteil der Systeme (z. B. ILIAS, Chamilo)
historisch fest an MySQL/MariaDB gekoppelt, während kommerzielle Suiten auf Oracle oder Microsoft SQL Server
setzten. 

Als herausragende Ausnahme der klassischen Open-Source-Linie gilt **[Moodle](https://github.com/moodle/moodle)**:
Moodle unterstützt PostgreSQL seit seinen frühen Versionen über eine eigene Abstraktionsschicht
(`pgsql`-Treiber) als vollwertige, produktionsreife Primärdatenbank für Großinstallationen.

---

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: 26. September 2026. Redaktionelle Auswahl nach der
[gemeinsamen Bewertungsmethode](software.md). Die Reihenfolge priorisiert
Reife und anschließend die Eignung für diese Kategorie.

| Rang | Software | Lizenz des Kerns | Reifegrad | Schwerpunkt | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Moodle](https://github.com/moodle/moodle) | GPL-3.0-or-later | Sehr hoch | Hochschul- und Schul-Lernplattformen | PostgreSQL: [Offizieller pgsql-Treiber](https://docs.moodle.org/all/de/PostgreSQL) |
| 2 | [Canvas LMS](https://github.com/instructure/canvas-lms) | AGPL-3.0 | Sehr hoch | Moderne akademische Lernplattformen | PostgreSQL: [Ausschließlich PostgreSQL](https://github.com/instructure/canvas-lms/wiki/Production-Start) |
| 3 | [Open edX](https://github.com/openedx/edx-platform) | AGPL-3.0 | Hoch | Skalierbare MOOC- und Online-Kurse | PostgreSQL: [Django-Backend für Core-Services](https://github.com/openedx/edx-platform) |
| 4 | [Sakai](https://github.com/sakaiproject/sakai) | ECL-2.0 | Hoch | Akademische Konsortien und Hochschulen | PostgreSQL: [Unterstützte relationale Datenbank](https://sakaiproject.atlassian.net/wiki/spaces/DOC/pages/38043653/Database+Configuration) |
| 5 | [Kolibri](https://github.com/learningequality/kolibri) | MIT | Hoch | Offline- und dateibasierte Bildungsumgebungen | Dateien: [Inhaltskanäle und Dateipakete](https://github.com/learningequality/kolibri) |

### 1. Moodle

**Begründung:** Weltweit am weitesten verbreitetes Open-Source-LMS mit mehr als zwei Jahrzehnten kontinuierlicher Entwicklung, riesigem Plugin-Ökosystem und nativer PostgreSQL-Unterstützung.

**Einordnung:** Monolithische Architektur mit historisch gewachsener Codebasis; Versionsupgrades erfordern sorgfältige Plugin-Prüfung.

Offizielle Grundlage: [Moodle](https://github.com/moodle/moodle).

### 2. Canvas LMS

**Begründung:** Führendes Hochschul-LMS mit moderner API-first-Architektur (Ruby on Rails); setzt in Produktion zwingend und ausschließlich auf PostgreSQL.

**Einordnung:** Hoher Ressourcenbedarf und komplexe Infrastruktur für den Eigenbetrieb; kommerzielle Leitlinie durch Instructure.

Offizielle Grundlage: [Canvas LMS](https://github.com/instructure/canvas-lms).

### 3. Open edX

**Begründung:** Etablierte Plattform für weltweite MOOCs (von MIT und Harvard initiiert); modular aufgebaut auf Python/Django mit PostgreSQL für relationale Kerndienste.

**Einordnung:** Für kleinere Bildungsträger überdimensioniert; erfordert dedizierte Betriebs- und DevOps-Kenntnisse (Tutor-Deployment).

Offizielle Grundlage: [Open edX](https://github.com/openedx/edx-platform).

### 4. Sakai

**Begründung:** Langjährig entwickeltes Java-LMS aus einem internationalen Hochschulkonsortium; strukturierte Kursverwaltung mit konfigurierbarer PostgreSQL-Anbindung.

**Einordnung:** Java-Serverbetrieb (Apache Tomcat) verlangt Fachadministration; Community im europäischen Raum kleiner als bei Moodle.

Offizielle Grundlage: [Sakai](https://github.com/sakaiproject/sakai).

### 5. Kolibri

**Begründung:** Dokumentierte Open-Source-Lernplattform von Learning Equality speziell für dateibasierte Offline-Nutzung an Schulen ohne Internetanschluss; Lehrpläne und Medien werden in Inhaltskanälen lokal gespeichert.

**Einordnung:** Konzentriert sich auf synchrone und asynchrone Offline-Lernszenarien; ersetzt kein universitäres Prüfungs- und Campusverwaltungssystem.

Offizielle Grundlage: [Kolibri](https://github.com/learningequality/kolibri).

---


## Verwandte Kapitel und Quellen

- **Quelle:** [Evolution und Architekturen digitaler klassischer LMS](https://dokument.wissen-ahrensburg.de/wissen/e-learning/evolution-digitaler-klassische-lms/) (Stand: 26. September 2026).
- [Evolution digitaler Wissenssysteme](wissenssysteme.md): Abgrenzung zwischen freier Wissensvernetzung und geführten Kursstrukturen.
- [Evolution digitaler Content-Management-Systeme](cms.md): Redaktionsprozesse im Vergleich zu Kursverwaltung.
- [Architekturen im Zusammenhang](architekturen.md): Das Zusammenspiel verschiedener Informationssysteme.
