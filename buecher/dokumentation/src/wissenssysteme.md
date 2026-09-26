# Evolution digitaler Wissenssysteme

Die Ausgangsseite beschreibt sechs sich überlappende Entwicklungsrichtungen.
Sie dienen als Orientierung und sind keine verbindliche Reifegradskala.

| Richtung | Zentrale Idee |
| --- | --- |
| Wikis | Seiten gemeinsam bearbeiten, versionieren und verlinken |
| Kollaborative Arbeitsräume und Docs-as-Code | Inhalte in gemeinsame Arbeitsabläufe einbetten |
| Persönliche Wissensgraphen und Block-Editoren | Kleine Wissenseinheiten und Rückverweise verbinden |
| Semantische und RAG-Systeme | Inhalte nach Bedeutung erschließen und für Antworten abrufen |
| Visuelle, Local-First und agentische Systeme | Wissen räumlich organisieren, lokal bearbeiten oder automatisiert pflegen |
| Multimodale Multi-Agenten-Systeme | Verschiedene Medien und spezialisierte Agenten zusammenführen |

Die späteren Richtungen ersetzen frühere nicht zwangsläufig. Für die Einordnung
sind auch Speicherform, Zusammenarbeit und Datenmodell entscheidend.

## Unterkategorien: gefilterte Softwareauswahl

- [Wiki-Systeme](wissenssysteme/wiki-systeme.md)
- [Kollaborative Arbeitsräume und Docs-as-Code](wissenssysteme/arbeitsraeume.md)
- [Persönliche Wissensgraphen und Block-Editoren](wissenssysteme/pkm.md)
- [Semantische und RAG-Systeme](wissenssysteme/semantische-systeme.md)
- [Visuelle, Local-First und agentische Systeme](wissenssysteme/local-first.md)
- [Multimodale Multi-Agenten-Systeme](wissenssysteme/multi-agenten.md)

## Geplante Vertiefung

- Von Seiten und Links zu Blöcken und Graphen
- Lokale Datenhaltung und gemeinsame Bearbeitung
- Quellenbezug und menschliche Prüfung bei KI-Unterstützung

Quelle: [Evolution und Architekturen digitaler Wissenssysteme](https://dokument.wissen-ahrensburg.de/wissen/dokumentation/evolution-digitaler-wissenssysteme/).

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: 26. September 2026. Redaktionelle Auswahl nach der
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

