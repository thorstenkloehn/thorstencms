# Digitale Wissenssysteme: Finden, Verknüpfen und Pflegen

Eine Sammlung wird dann im Alltag nützlich, wenn Menschen die passende
Information wiederfinden und erkennen können, ob sie noch gilt. Dafür braucht
es neben der Suche auch Zuständigkeiten, Änderungsverläufe und eine verständliche
Ordnung. Ein Wissenssystem verbindet diese Aufgaben; seine Oberfläche allein
sagt noch wenig über die Qualität des Bestands aus.

## Entscheidungen am Beispiel eines Projektwissens

Ein Team hält zunächst Entscheidungen und Betriebserfahrungen auf Wiki-Seiten
fest. Jede Entscheidung erhält einen Anlass, eine verantwortliche Person und
Verweise auf betroffene Komponenten. Persönliche Notizen können daneben lokal
bleiben. Erst ausgewählte, überprüfte Erkenntnisse werden in den Teambestand
übernommen.

Mit wachsendem Umfang wird die Suche wichtiger. Schlagwörter, Volltextsuche
und semantische Verfahren erfüllen unterschiedliche Aufgaben. Ein RAG-Ablauf
kann passende Passagen für einen Antwortentwurf bereitstellen. Ob die Antwort
diese Passagen korrekt wiedergibt, muss gesondert geprüft werden.

## Architekturfragen

- Liegen Inhalte zentral oder auf den Endgeräten?
- Werden Seiten, einzelne Blöcke oder strukturierte Datensätze bearbeitet?
- Wie werden widersprüchliche Änderungen erkannt und entschieden?
- Werden Zugriffsrechte bereits beim Abruf von Suchergebnissen durchgesetzt?
- Wie werden veraltete Informationen gekennzeichnet oder entfernt?

Die folgenden Kategorien sind sich überschneidende Arbeitsweisen. Sie bilden
keine feste Abfolge, in der eine neue Technik ältere Systeme ersetzt.

## Unterkategorien: gefilterte Softwareauswahl

- [Wiki-Systeme](wissenssysteme/wiki-systeme.md)
- [Kollaborative Arbeitsräume](wissenssysteme/arbeitsraeume.md)
- [Persönliche Wissensorganisation](wissenssysteme/pkm.md)
- [Semantische und RAG-Systeme](wissenssysteme/semantische-systeme.md)
- [Lokale und visuelle Werkzeuge](wissenssysteme/local-first.md)
- [Multi-Agenten-Bausteine](wissenssysteme/multi-agenten.md)

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: 27. September 2026. Auswahl nach der
[gemeinsamen Bewertungsmethode](software.md). Die Reihenfolge priorisiert
Reife und anschließend die Eignung für diese Kategorie.

| Rang | Software | Lizenz des Kerns | Reifegrad | Schwerpunkt | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [MediaWiki](https://github.com/wikimedia/mediawiki) | GPL-2.0-or-later | Sehr hoch | Große, vernetzte Wissenssammlungen | PostgreSQL: [PostgreSQL](https://www.mediawiki.org/wiki/Manual:PostgreSQL/en) |
| 2 | [XWiki](https://www.xwiki.org/xwiki/bin/view/Main/) | LGPL-2.1 | Sehr hoch | Unternehmenswissen und strukturierte Wiki-Anwendungen | PostgreSQL: [PostgreSQL](https://www.xwiki.org/xwiki/bin/view/Documentation/AdminGuide/Installation/InstallationWAR/InstallationPostgreSQL/) |
| 3 | [DokuWiki](https://github.com/dokuwiki/dokuwiki) | GPL-2.0 | Sehr hoch | Überschaubare Dokumentations-Wikis | Dateien: [Textdateien und Medienverzeichnisse](https://github.com/dokuwiki/dokuwiki) |
| 4 | [TiddlyWiki](https://github.com/TiddlyWiki/TiddlyWiki5) | BSD-3-Clause | Hoch | Persönliches und portables Wissen | Dateien: [Einzelne HTML-Datei mit eingebetteten Inhalten](https://tiddlywiki.com/dev/static/Data%2520Storage%2520in%2520Single%2520File%2520TiddlyWiki.html) |
| 5 | [Wiki.js](https://js.wiki/about) | AGPL-3.0 | Hoch | Moderne Dokumentations- und Wissensportale | PostgreSQL: [Unterstütztes Datenbank-Backend](https://js.wiki/get-started) |

### 1. MediaWiki

**Begründung:** Betrieb der Wikimedia-Projekte und dokumentierter LTS- sowie Upgrade-Zyklus.

**Einordnung:** Erweiterungen und Upgrades müssen gemeinsam geplant werden.

Offizielle Grundlage: [MediaWiki](https://github.com/wikimedia/mediawiki).

### 2. XWiki

**Begründung:** Langjährig entwickelte Plattform mit Anwendungsmodell, Erweiterungen und umfangreicher Dokumentation.

**Einordnung:** Individuelle Wiki-Anwendungen erhöhen den Betriebsaufwand.

Offizielle Grundlage: [XWiki](https://www.xwiki.org/xwiki/bin/view/Main/).

### 3. DokuWiki

**Begründung:** Seit 2004 entwickelte Wiki-Engine mit dokumentierter Installation, Community und Sicherheitsrichtlinie.

**Einordnung:** Kompatibilität zusätzlicher Plugins gesondert prüfen.

Offizielle Grundlage: [DokuWiki](https://github.com/dokuwiki/dokuwiki).

### 4. TiddlyWiki

**Begründung:** Langjähriges Wiki-Projekt mit eigenständigem Browser- und Node.js-Betrieb sowie offenem Entwicklungsprozess.

**Einordnung:** Gemeinsame Bearbeitung und Synchronisierung brauchen ein passendes Betriebskonzept.

Offizielle Grundlage: [TiddlyWiki](https://github.com/TiddlyWiki/TiddlyWiki5).

### 5. Wiki.js

**Begründung:** Dokumentiertes Wiki mit visueller Bearbeitung und mehreren Speicherintegrationen.

**Einordnung:** Für diese Auswahl PostgreSQL als Anwendungsdatenbank konfigurieren. Zusätzliche Speicherziele sind optional und nicht Bestandteil der gewählten Variante.

Offizielle Grundlage: [Wiki.js](https://js.wiki/about).
