# KI- und CLI-Coding-Agenten im Vergleich

Ein Werkzeug im Terminal kann Befehle erklären, Dateien ändern oder ganze
Arbeitsabläufe bearbeiten. Diese Fähigkeiten sind keine festen historischen
Generationen. Ein Produkt kann mehrere davon kombinieren; Version,
Konfiguration und eingeräumte Rechte bestimmen den verfügbaren Umfang.

## Fähigkeiten statt Generationen

| Fähigkeit | Nutzen für ein Buchprojekt | Zu prüfende Grenze |
| --- | --- | --- |
| Befehlsassistenz | Einen Build-Befehl erläutern oder einen Suchausdruck entwerfen | Ein Vorschlag ist noch nicht ausgeführt oder geprüft. |
| Repository-Bearbeitung | Artikel, Navigation und Verweise zusammen ändern | Änderungen brauchen Diff-Kontrolle und fachliche Prüfung. |
| Werkzeugausführung | Build-Ergebnisse oder Fehlermeldungen auswerten | Ausführung hängt von der Umgebung und den Berechtigungen ab. |
| Delegation | Recherche oder Prüfung in getrennten Kontexten bearbeiten | Ergebnisse müssen zusammengeführt und Widersprüche geklärt werden. |

## Dokumentierte Beispiele

**Codex CLI** kann ein Projekt untersuchen, Dateien bearbeiten und Befehle
in der eingerichteten Umgebung ausführen. Die Einordnung als bloßer
Befehlshelfer trifft darauf nicht zu. [Offizielle Codex-Dokumentation](https://learn.chatgpt.com/docs/codex/cli).

**Claude Code** dokumentiert Subagenten mit eigenem Kontext und konfigurierbaren
Werkzeugen. Die Behauptung, solche Aufgaben seien grundsätzlich nicht entkoppelt
möglich, ist daher unzutreffend. [Claude Code: Subagenten](https://code.claude.com/docs/en/sub-agents).

**Aider** unterstützt die Arbeit an Repository-Dateien; **Cline** bietet eine
Agentenumgebung für Änderungen und Werkzeugaufrufe. Ihre konkrete Nutzung und
Persistenz sind in der [Auswahl zur Dokumentationspflege](docs-as-code/agentische-pflege.md)
verlinkt. **LangGraph** ist dagegen ein Framework, mit dem eigene Abläufe gebaut
werden können. Eine fertige Terminal-Oberfläche oder Buchredaktion folgt daraus
nicht automatisch.

## Beispiel: Einen Artikel aktualisieren

Zunächst werden Aussage und Quellen geprüft. Anschließend werden Text,
Tabelleneintrag und Querverweise gemeinsam überarbeitet. Ein Build kontrolliert
die technische Ausgabe. Zum Schluss werden die Änderungen mit den Quellen
verglichen. Ein erfolgreicher Build erkennt keine falsche Lizenzangabe.

Für parallele Bearbeitung sollten Aufgaben möglichst getrennte Dateien
betreffen. Wenn mehrere Agenten dieselbe Passage ändern, braucht es eine
bewusste Entscheidung über die endgültige Fassung.

Die hier beschriebenen Produktfähigkeiten wurden dokumentenbasiert am
27. September 2026 geprüft. Es handelt sich nicht um einen Leistungstest oder
um eine Aussage über die Lizenz der jeweils angeschlossenen Modelle.
