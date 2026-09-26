# Mobile Bildungs- und E-Learning-Apps

[Übergeordnete Kategorie: Mobile und Desktop-Apps in Content- und Wissenssystemen](../mobile-desktop-apps.md)

Lern- und Kursbegleiter auf Smartphones und Tablets mit Offline-Fähigkeit und Notenabgleich.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Moodle App](https://github.com/moodlehq/moodleapp) | GPL-3.0-or-later | Sehr hoch | Weltweit etablierte Kurs-App mit Offline-Download und asynchronem Notenabgleich. | PostgreSQL: [Moodle-Backend mit PostgreSQL-Persistenz](https://docs.moodle.org/all/de/PostgreSQL) |
| 2 | [Canvas Student](https://github.com/instructure/canvas-android) | AGPL-3.0 | Sehr hoch | Native mobile App für Lernende an Universitäten mit Kurskalender und Abgaben. | PostgreSQL: [Canvas-Backend auf PostgreSQL-Basis](https://github.com/instructure/canvas-lms/wiki/Production-Start) |
| 3 | [Kolibri](https://github.com/learningequality/kolibri) | MIT | Hoch | Plattformübergreifende Offline-Lern-App für Android und Desktop. | Dateien: [Lokale Inhaltskanäle und Dateipakete](https://github.com/learningequality/kolibri) |
| 4 | [Open edX Mobile](https://github.com/openedx/edx-app-android) | Apache-2.0 | Hoch | Offizielle mobile App für MOOC-Teilnehmer mit Videodownloads und Modulabschluss. | PostgreSQL: [Open edX Core-Services auf PostgreSQL](https://github.com/openedx/edx-platform) |
| 5 | [BigBlueButton Mobile](https://github.com/bigbluebutton/bigbluebutton) | LGPL-3.0 | Sehr hoch | Responsive mobile Hörsaal- und Seminarumgebung für Blended Learning. | Dateien: [Dateibasierte Medien- und Aufzeichnungsablage](https://docs.bigbluebutton.org/) |

## Einsatz und Abgrenzung

Mobile Lern-Apps ergänzen den Desktop-Campus um ortsunabhängiges Lernen und Push-Benachrichtigungen.

- **Moodle App:** Basiert auf Capacitor/Ionic; setzt aktivierte Webdienste auf der Moodle-Instanz voraus.
- **Canvas Student:** Native Benutzeroberfläche; Bindung an das Canvas-LMS-Backend.
- **Kolibri:** Konzipiert für dezentrale Schulen; kein vollwertiges Prüfungs- und Immatrikulationssystem.
- **Open edX Mobile:** Spezialisiert auf strukturierte Online-Kurse; hohes Datenvolumen bei Videoinhalten.
- **BigBlueButton Mobile:** Live-Audio und Präsentationen direkt im mobilen Browser ohne App-Store-Download.
