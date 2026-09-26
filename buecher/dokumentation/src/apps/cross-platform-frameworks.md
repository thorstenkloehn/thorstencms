# Cross-Platform-App-Frameworks

[Übergeordnete Kategorie: Mobile und Desktop-Apps in Content- und Wissenssystemen](../mobile-desktop-apps.md)

Laufzeitumgebungen und Entwicklungsframeworks für plattformübergreifende Clients im Wissens- und Content-Bereich.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Tauri](https://github.com/tauri-apps/tauri) | Apache-2.0 | Sehr hoch | Extrem ressourcenschonende Multi-Plattform-Laufzeit (Rust + Web-Frontend) für Desktop und Mobile. | Dateien: [Lokaler Dateisystem- und SQLite-Zugriff](https://tauri.app/) |
| 2 | [React Native](https://github.com/facebook/react-native) | MIT | Sehr hoch | Etablierter Standard für native iOS- und Android-Apps mit Web-Technologien. | Dateien: [Lokaler SQLite- und Dateispeicher über offizielle Module](https://reactnative.dev/) |
| 3 | [Flutter](https://github.com/flutter/flutter) | BSD-3-Clause | Sehr hoch | Plattformübergreifend kompilierte UI-Engine für Mobile, Desktop und Web. | Dateien: [Lokale Dateipersistenz und sqflite](https://flutter.dev/) |
| 4 | [Capacitor](https://github.com/ionic-team/capacitor) | MIT | Sehr hoch | Moderne native Bridge zur Auslieferung von Web-Apps auf mobilen Betriebssystemen. | Dateien: [Lokaler Dateispeicher und SQLite-Plugins](https://capacitorjs.com/) |
| 5 | [Electron](https://github.com/electron/electron) | MIT | Sehr hoch | Führendes Desktop-Framework (Chromium + Node.js) für Apps wie Joplin, Obsidian und VS Code. | Dateien: [Vollständiger Node.js-Dateisystemzugriff](https://www.electronjs.org/) |

## Einsatz und Abgrenzung

Entwicklungsframeworks stellen die technische Brücke zwischen Webcode und Betriebssystem her.

- **Tauri:** Minimale Binary-Größe und hohe Sicherheit; erfordert für native Systemfunktionen Rust-Kenntnisse.
- **React Native:** Zugriff auf native Plattformkomponenten; Build-Pipelines (Xcode/Android Studio) sind zu pflegen.
- **Flutter:** Identische Pixel-Darstellung auf allen Geräten; erfordert die Programmiersprache Dart.
- **Capacitor:** Einfachste Migration bestehender Webanwendungen; Performance hängt von der WebView ab.
- **Electron:** Bewährteste Desktop-Laufzeit; höherer Speicher- und Ressourcenverbrauch als Tauri.
