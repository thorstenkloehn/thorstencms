# Sprachmodelle in Lernmanagement-Systemen

[Übergeordnete Kategorie: Integration von Sprachmodellen in Software-Architekturen](../sprachmodell-integration.md)

KI-gestützte Tutoren, adaptive Lernpfade, automatische Fragen-Generierung und didaktisches Feedback.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Moodle](https://github.com/moodle/moodle) | GPL-3.0-or-later | Sehr hoch | Offizielles modulares KI-Subsystem mit Provider-Plugins für Zusammenfassungen und Textgenerierung. | PostgreSQL: [Offizieller pgsql-Treiber](https://docs.moodle.org/all/de/PostgreSQL) |
| 2 | [Canvas LMS](https://github.com/instructure/canvas-lms) | AGPL-3.0 | Sehr hoch | Ausgereifte LTI-1.3-Schnittstellen zur nahtlosen Einbindung externer KI-Tutoren und Feedback-Bots. | PostgreSQL: [Ausschließlich PostgreSQL](https://github.com/instructure/canvas-lms/wiki/Production-Start) |
| 3 | [Open edX](https://github.com/openedx/edx-platform) | AGPL-3.0 | Hoch | Modulare Plattform mit Schnittstellen für automatische Testgenerierung und KI-Didaktik. | PostgreSQL: [Core-Services auf PostgreSQL](https://github.com/openedx/edx-platform) |
| 4 | [Kolibri](https://github.com/learningequality/kolibri) | MIT | Hoch | Offline-Lernplattform mit Erprobung lokaler Small Language Models (SLMs) für ressourcenarme Schulen. | Dateien: [Inhaltskanäle und lokale Pakete](https://github.com/learningequality/kolibri) |
| 5 | [H5P](https://github.com/h5p) | MIT | Sehr hoch | Standard für interaktive Übungen; unterstützt KI-Autoren-Workflows für automatisierte Aufgabenerstellung. | Dateien: [Dateibasierte H5P-Pakete (.h5p)](https://h5p.org/documentation) |

## Einsatz und Abgrenzung

Didaktische KI-Systeme müssen Transparenz und Datenschutz im Lernkontext gewährleisten.

- **Moodle:** KI-Funktionen sind rollenbasiert aktivierbar; Datenschutzrichtlinien (Art. 50 EU AI Act) beachten.
- **Canvas LMS:** Bindet KI primär über LTI-Werkzeuge ein; Datenflüsse zu Drittanbietern müssen vertraglich geregelt sein.
- **Open edX:** Ermöglicht großskalierte automatisierte Bewertungen; erfordert sorgfältige Prüfungsüberwachung.
- **Kolibri:** Konzentriert sich auf datenschutzkonforme Offline-Nutzung; lokale Sprachmodelle benötigen passende Hardware.
- **H5P:** Ermöglicht schnelle Generierung interaktiver Formate (z. B. Lückentexte, Quizze); erfordert didaktische Qualitätsprüfung.
