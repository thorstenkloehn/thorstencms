# Mobile Bildungs- und E-Learning-Apps

[Übergeordnete Kategorie: Mobile und Desktop-Apps in Content- und Wissenssystemen](../mobile-desktop-apps.md)

Lern- und Kursbegleiter auf Smartphones und Tablets mit Offline-Fähigkeit und Notenabgleich.

## Open-Source-Auswahl nach Reifegrad

**2 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Moodle App](https://github.com/moodlehq/moodleapp) | GPL-3.0-or-later | Sehr hoch | Client für Kurszugriff; verfügbare Offline-Aktivitäten separat prüfen. | PostgreSQL nur serverseitig: [Moodle-Backend mit PostgreSQL-Persistenz](https://docs.moodle.org/all/de/PostgreSQL) |
| 2 | [Canvas Student](https://github.com/instructure/canvas-android) | AGPL-3.0 | Sehr hoch | Native mobile App für Lernende an Universitäten mit Kurskalender und Abgaben. | PostgreSQL nur serverseitig: [Canvas-Backend auf PostgreSQL-Basis](https://github.com/instructure/canvas-lms/wiki/Production-Start) |

## Einsatz und Abgrenzung

Moodle App und Canvas Student werden als Clients ihrer jeweiligen
Lernplattform betrachtet. Die PostgreSQL-Angabe bezeichnet ausschließlich den
Serverbestand. Lokale Datenbanken, Offline-Änderungen und externe Push-Dienste
sind damit nicht als Teil einer vollständig PostgreSQL-/dateibasierten
Gesamtinstallation nachgewiesen.

Vor dem Einsatz wird ein Beispielkurs auf den vorgesehenen Endgeräten geprüft:
Welche Inhalte sind offline verfügbar? Wie werden ausstehende Abgaben angezeigt?
Was geschieht nach einer erneuten Anmeldung oder einem Übertragungsfehler?
Aus der PostgreSQL-Unterstützung des Servers folgt keine Antwort auf diese Fragen.
