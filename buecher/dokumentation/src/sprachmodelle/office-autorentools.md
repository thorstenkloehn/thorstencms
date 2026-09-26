# Sprachmodelle in Office- und Autorentools

[Übergeordnete Kategorie](../sprachmodell-integration.md)

Die Auswahl beschreibt eine konkret dokumentierte Plugin-Anbindung für lokale Bürodokumente.

## Open-Source-Auswahl nach Reifegrad

**1 Eintrag:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**. [Bewertungskriterien und Grenzen](../software.md).

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [ONLYOFFICE Desktop Editors](https://github.com/ONLYOFFICE/DesktopEditors) | AGPL-3.0 | Hoch | Desktop-Editoren mit dokumentiertem KI-Plugin. | Dateien: [Lokale Bürodokumente](https://github.com/ONLYOFFICE/DesktopEditors) |

## Einsatz und Abgrenzung

Das [KI-Plugin](https://api.onlyoffice.com/docs/ai/guides/ai-plugin/) verbindet
Editorfunktionen mit einem ausgewählten Modellanbieter. Anbieter, Modell und
gegebenenfalls API-Schlüssel werden in den Plugin-Einstellungen konfiguriert.
Eine pauschale zentrale Schlüsselablage im Document Server wird hier nicht behauptet.

Ein mögliches Vorgehen ist, einen Absatz zu markieren, eine Überarbeitung
anzufordern und den Vorschlag vor dem Speichern zu prüfen. Die Speicherung
des Dokuments als lokale Datei sagt nichts darüber aus, ob der markierte Text
zur Verarbeitung an einen externen Dienst übertragen wird.

LibreOffice, Etherpad, CryptPad und Zettlr werden in dieser Kategorie nicht
als Produkte mit nachgewiesenen integrierten Sprachmodellfunktionen geführt.
Eigene Skripte oder Erweiterungen sind denkbar, benötigen aber einen konkreten
Funktions-, Versions- und Datenspeichernachweis. Die Eignung als Schreibwerkzeug
ist davon unabhängig.
