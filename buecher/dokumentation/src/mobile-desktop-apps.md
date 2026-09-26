# Mobile und Desktop-Apps in Content- und Wissenssystemen

Apps ergänzen die Arbeit im Browser, etwa beim Schreiben ohne Verbindung,
beim Zugriff auf lokale Dateien oder bei der Aufnahme von Medien. Ob eine
App dafür geeignet ist, hängt von ihren konkreten Funktionen und vom
angeschlossenen Server ab. Auch Webanwendungen können Offline-Funktionen bieten.

## Beispiel: Unterwegs eine Notiz bearbeiten

Eine Person ändert eine Notiz auf dem Laptop und später auf dem Smartphone.
Die Anwendung muss die Änderungen dauerhaft speichern und beim nächsten
Abgleich zusammenführen oder einen Konflikt anzeigen. Eine erfolgreiche
Übertragung allein belegt noch nicht, dass die fachlich gewünschte Fassung
entstanden ist. Eine wiederherstellbare Historie bleibt sinnvoll.

## Drei getrennte Speicherfragen

| Frage | Bedeutung für die Auswahl |
| --- | --- |
| Wo liegt der vollständige Inhalt? | Direkte Inhaltsdateien oder PostgreSQL müssen den betrachteten Bestand tragen. |
| Was wird nur zwischengespeichert? | Ein Medien-Cache oder Export macht eine datenbankgestützte Anwendung nicht dateibasiert. |
| Wo liegen noch nicht synchronisierte Änderungen? | Lokale Änderungen sind maßgebliche Daten, solange sie nur auf dem Endgerät existieren. |

Joplin speichert auch Notizen in SQLite und wird deshalb nicht als
Markdown-Dateianwendung in der gefilterten Tabelle geführt.
[Joplin: Architektur](https://joplinapp.org/help/dev/spec/architecture/).

Moodle App wird hier als Client eines PostgreSQL-basierten Moodle-Servers
betrachtet. Die Aussage betrifft den Serverbestand; die gesamte Offline-App
ist damit nicht als SQLite-frei bewertet. Diesen Unterschied benennt die Tabelle.

## Synchronisation und Zugriffsrechte

CRDT-Bibliotheken können nebenläufige Änderungen nach ihren Regeln zusammenführen.
Sie garantieren weder einen fachlich sinnvollen Text noch Schutz vor Löschung,
Geräteausfall oder Fehlern in der Integration. Git kann Konflikte melden, die
anschließend von Menschen gelöst werden müssen.

Ein Server prüft bei jeder relevanten Anfrage Anmeldung und Berechtigung.
Datenbankzugangsdaten gehören nicht in einen verteilten Client. Bei einer
OAuth-Anbindung öffentlicher Clients dient PKCE dem Schutz des Autorisierungscodes;
PKCE ist selbst kein biometrisches Anmeldeverfahren.

## Unterkategorien: gefilterte Softwareauswahl

- [Persönliche Wissens-Apps](apps/pkm-notizen.md)
- [Mobile Lern-Apps](apps/lms-mobile.md)
- [Redaktions-Clients](apps/cms-clients.md)
- [Plattformübergreifende Frameworks](apps/cross-platform-frameworks.md)
- [Synchronisationsbausteine](apps/offline-sync.md)

## Open-Source-Auswahl nach Reifegrad

**3 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: 27. September 2026. Auswahl nach der
[gemeinsamen Bewertungsmethode](software.md). Die Reihenfolge priorisiert
Reife und anschließend die Eignung für diese Kategorie.

| Rang | Software | Lizenz des Kerns | Reifegrad | Schwerpunkt | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Moodle App](https://github.com/moodlehq/moodleapp) | GPL-3.0-or-later | Sehr hoch | Mobile Lern- und Kurs-App mit Offline-Synchronisation | PostgreSQL nur serverseitig: [Moodle-Backend mit PostgreSQL-Persistenz](https://docs.moodle.org/all/de/PostgreSQL) |
| 2 | [SiYuan](https://github.com/siyuan-note/siyuan) | AGPL-3.0 | Hoch | Block-basierter persönlicher Wissensgraph (Desktop & Mobile) | Dateien: [Lokales JSON-Dateisystem im Arbeitsbereich](https://github.com/siyuan-note/siyuan/blob/master/docs/WORKSPACE.md) |
| 3 | [Tauri](https://github.com/tauri-apps/tauri) | MIT; teilweise MIT OR Apache-2.0 | Hoch | Rust-Kern und Weboberfläche; eigene Anwendungslogik erforderlich. | Dateien: [File-System-Plugin mit eingeschränkten Berechtigungen](https://v2.tauri.app/plugin/file-system/) |

## Praktische Auswahl

SiYuan wird wegen seiner lokalen Inhaltsdateien betrachtet. Tauri ist dagegen
ein Framework: Dateiformat, Speicherung und Benutzeroberfläche werden für die
eigene Anwendung entwickelt. Eine Datei-API belegt diese Möglichkeit, aber
keine fertige Wissensverwaltung.

Für eine mobile Lernlösung sollte vor dem Einsatz geklärt werden, welche
Kursaktivitäten offline funktionieren und wie fehlgeschlagene Übertragungen
angezeigt werden. Die Eignung des Servers reicht als Nachweis dafür nicht aus.
