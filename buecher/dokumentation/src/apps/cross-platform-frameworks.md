# Cross-Platform-App-Frameworks

[Übergeordnete Kategorie: Mobile und Desktop-Apps in Content- und Wissenssystemen](../mobile-desktop-apps.md)

Laufzeitumgebungen und Entwicklungsframeworks für plattformübergreifende Clients im Wissens- und Content-Bereich.

## Open-Source-Auswahl nach Reifegrad

**4 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Flutter](https://github.com/flutter/flutter) | BSD-3-Clause | Sehr hoch | Framework für plattformübergreifende Oberflächen. | Dateien: [Lesen und Schreiben mit dart:io und path_provider](https://docs.flutter.dev/cookbook/persistence/reading-writing-files) |
| 2 | [Capacitor](https://github.com/ionic-team/capacitor) | MIT | Sehr hoch | Native Laufzeit und Plugins für Weboberflächen. | Dateien: [Filesystem-Plugin](https://capacitorjs.com/docs/apis/filesystem) |
| 3 | [Electron](https://github.com/electron/electron) | MIT | Sehr hoch | Desktop-Laufzeit mit Browser- und Node.js-Prozessen. | Dateien: [Dateizugriff im Hauptprozess, begrenzte IPC-Anbindung](https://www.electronjs.org/docs/latest/tutorial/tutorial-preload) |
| 4 | [Tauri](https://github.com/tauri-apps/tauri) | MIT; teilweise MIT OR Apache-2.0 | Hoch | Rust-Kern und Weboberfläche; eigene Anwendungslogik erforderlich. | Dateien: [File-System-Plugin mit eingeschränkten Berechtigungen](https://v2.tauri.app/plugin/file-system/) |

## Einsatz und Abgrenzung

Die Auswahl bewertet Frameworks für selbst entwickelte Anwendungen. Ein
Dateispeicher muss tatsächlich implementiert werden; SQLite-Plugins werden
hier nicht als zulässiger Ersatz für Inhaltsdateien aufgeführt.

Die Dateizugriffe unterscheiden sich nach Plattform und Berechtigungen.
Der verlinkte Flutter-Ablauf gilt nicht für den Browser. Electron führt
privilegierte Dateizugriffe auf der Anwendungsseite aus; eine beliebige
Webseite erhält dadurch keinen unbeschränkten Zugriff auf das Dateisystem.

Für ein Beispielprojekt werden zunächst Textdateien gespeichert, nach einem
Neustart geladen und bei fehlenden Schreibrechten verständliche Fehlermeldungen
angezeigt. Synchronisation und Konfliktbehandlung sind zusätzliche Aufgaben.
