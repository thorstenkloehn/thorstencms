# Sprachmodelle in Office- und Autorentools

[Übergeordnete Kategorie: Integration von Sprachmodellen in Software-Architekturen](../sprachmodell-integration.md)

Assistierte Texterstellung, Dokumentenzusammenfassung, interaktive Echtzeit-Kollaboration und sprachmodellgestützte Autoren-Workflows für Wissens- und Bürodokumente.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [LibreOffice](https://github.com/LibreOffice/core) | MPL-2.0 | Sehr hoch | Etablierte Open-Source-Office-Suite mit flexibler Erweiterungsarchitektur für sprachmodellgestützte Texterstellung und Übersetzung. | Dateien: [Lokale Dokumentdateien (ODT, DOCX) und Erweiterungsdateien](https://www.libreoffice.org/) |
| 2 | [ONLYOFFICE Docs](https://github.com/ONLYOFFICE/DocumentServer) | AGPL-3.0 | Sehr hoch | Kollaborative Online-Office-Suite mit offiziellem KI-Plugin für Textgenerierung, Zusammenfassung und Übersetzung direkt im Bearbeitungsfenster. | PostgreSQL: [PostgreSQL als zentrale Datenbank für Document Server](https://helpcenter.onlyoffice.com/server/linux/document/linux-installation.aspx) |
| 3 | [Etherpad](https://github.com/ether/etherpad-lite) | Apache-2.0 | Sehr hoch | Echtzeit-Editor für kollaboratives Schreiben mit nativer Plugin-Architektur für KI-Assistenten und Texttransformationen. | PostgreSQL: [PostgreSQL als relationale Produktionsdatenbank (ueberdb2)](https://etherpad.org/doc/v2.2.0/) |
| 4 | [CryptPad](https://github.com/cryptpad/cryptpad) | AGPL-3.0 | Hoch | Ende-zu-Ende verschlüsselte Office-Suite mit Rich-Text-, Markdown- und Tabellen-Editoren und dateibasiertem Betrieb. | Dateien: [Dateibasiertes Datastore-Verzeichnis auf dem Server](https://docs.cryptpad.org/) |
| 5 | [Zettlr](https://github.com/Zettlr/Zettlr) | GPL-3.0 | Hoch | Spezialisierter Markdown-Editor für Autoren und Wissenschaftler mit Zettelkasten-System, Zitationsverwaltung und KI-Workflows. | Dateien: [Lokale Markdown-Dateien und YAML-Metadaten](https://docs.zettlr.com/) |

## Einsatz und Abgrenzung

Office-Suiten und Autorentools nutzen Sprachmodelle zur Textverdichtung und Strukturierung, verlangen jedoch strikten Schutz vertraulicher Inhalte.

- **LibreOffice:** Erlaubt vollständig isolierten Offline-Betrieb über lokale Modelle (z. B. via Ollama); erfordert die Installation passender Python-Skripte oder Erweiterungen.
- **ONLYOFFICE Docs:** Bietet nahtlose Einbettung in Web-Arbeitsumgebungen; API-Schlüssel für KI-Dienste werden zentral im Document Server hinterlegt.
- **Etherpad:** Ideal für simultanes kollaboratives Verfassen von Texten; KI-Plugins unterstützen Autoren in Echtzeit bei Gliederungen und Formulierungen.
- **CryptPad:** Fokussiert auf kryptografische Vertraulichkeit; KI-Funktionen müssen datenschutzkonform ohne Abfluss sensibler Entwürfe an Dritte betrieben werden.
- **Zettlr:** Maßgeschneidert für akademische Langform-Autoren; verbindet Markdown-Dateien, Literaturverzeichnisse und Sprachmodell-Analysen.
