# Softwareauswahl und Reifegrade

Die acht Hauptkategorien und 52 Unterkategorien enthalten ausschließlich
Open-Source-Software mit einem passenden PostgreSQL- oder Dateibetrieb.
Jede der 60 Kategorien enthält genau fünf passende Projekte. Insgesamt sind das
300 Listeneinträge für 129 unterschiedliche Projekte; Mehrfachnennungen über
verschiedene Kategorien hinweg sind beabsichtigt.
Stand der Quellenprüfung: **26. September 2026**.

- [Dokumentenerstellung, Wikis und Notebooks](dokumentation.md#open-source-auswahl-nach-reifegrad)
- [Wissenssysteme](wissenssysteme.md#open-source-auswahl-nach-reifegrad)
- [Content-Management-Systeme](cms.md#open-source-auswahl-nach-reifegrad)
- [Docs-as-Code](docs-as-code.md#open-source-auswahl-nach-reifegrad)
- [Webframeworks](webframeworks.md#open-source-auswahl-nach-reifegrad)
- [Lernmanagement-Systeme](klassische-lms.md#open-source-auswahl-nach-reifegrad)
- [Mobile und Desktop-Apps](mobile-desktop-apps.md#open-source-auswahl-nach-reifegrad)
- [Integration von Sprachmodellen](sprachmodell-integration.md#open-source-auswahl-nach-reifegrad)

## Verbindlicher Speicherfilter

Ein Eintrag bleibt nur für einen dokumentierten Betrieb mit **PostgreSQL**
oder **direkten Inhaltsdateien** erhalten. Die Tabellen nennen die gewählte
Variante und verlinken ihren Nachweis. Andere unterstützte Backends desselben
Produkts sind nicht Teil dieser Auswahl.

- **PostgreSQL:** Inhalte oder der betrachtete Framework-Zustand können in
  PostgreSQL gespeichert werden. Bei Vektorsuche ist gegebenenfalls pgvector
  einzurichten. Ein bloßer Import aus PostgreSQL reicht nicht.
- **Dateien:** Die maßgeblichen Inhalte liegen beispielsweise in Markdown,
  JSON, HTML, Org, AsciiDoc, Notebooks oder Dokumentdateien. Git-basierte
  Inhaltsverwaltung und dateibasierte Generatoren sind eingeschlossen.
- **SQLite als Hauptspeicher** ist in dieser Auslegung nicht eingeschlossen.
  Rekonstruierbare Hilfsindizes sind zulässig, wenn die vollständigen Inhalte
  unabhängig davon in Dateien liegen. Das trifft auf die dokumentierten
  Speicherwege von [Org-roam](https://www.orgroam.com/manual) und
  [SiYuan](https://github.com/siyuan-note/siyuan/blob/master/docs/WORKSPACE.md) zu.
- **Frameworks:** Die genannte Speicherintegration muss ausdrücklich gewählt
  werden. Bei zusätzlichen Daten, Chat-Historien und Indizes ist derselbe
  Filter anzuwenden. Eine In-Memory-Demo ist kein Persistenznachweis.

Erforderliche andere Datenbanken und nicht belegte Speicherwege führen zum
Entfernen des Eintrags. Datei-Import, Export, Backup oder Zugriff auf eine
fremde Datenbank allein machen eine Anwendung nicht dateibasiert.

**Sonderfall AnythingLLM:** Das Projekt beschreibt die Umstellung der
Anwendungsdatenbank auf PostgreSQL im
[Prisma-Schema](https://github.com/Mintplex-Labs/anything-llm/blob/master/server/prisma/schema.prisma).
Zusätzlich ist [pgvector](https://github.com/Mintplex-Labs/anything-llm/blob/master/server/utils/vectorDbProviders/pgvector/SETUP.md)
für Vektordaten einzurichten. Nur diese angepasste Variante bleibt enthalten;
ihre Reife wird wegen des Anpassungsbedarfs als mittel eingestuft.
Die Umstellung wurde hier nicht praktisch erprobt.

## Bewertungsmethode

Die Auswahl ist eine redaktionelle Empfehlung aus den geprüften Projekten,
keinen vollständigen Marktvergleich. Die Reifegrade sind qualitative Urteile,
keine Zertifizierung und keine gemessenen TRL-Werte. Grundlage sind die
verlinkten offiziellen Projektseiten, Repositories und Handbücher.

Für die Auswahl zählen:

1. **Offene Lizenz:** Der aufgeführte Softwarekern steht unter einer Open-Source-Lizenz.
2. **Wartung:** Öffentliche Entwicklung, Änderungsverläufe und ein erkennbarer Pflegeprozess.
3. **Dokumentation:** Beschriebene Nutzung, Konfiguration und gegebenenfalls Betrieb.
4. **Bewährung:** Langjährige Entwicklung oder dokumentierte produktive Verwendung.
5. **Pflegbarkeit:** Nachvollziehbare Aktualisierung, Community und projektgerechte Erweiterbarkeit.

**Sehr hoch** bedeutet hier: langjährig etablierte Grundlage mit umfangreicher
Dokumentation und belastbaren Hinweisen auf kontinuierliche Pflege oder
produktiven Einsatz. **Hoch** bedeutet: ausgereifte, dokumentierte Lösung,
deren Eignung stärker auf einen bestimmten Einsatzbereich zugeschnitten ist
oder deren Betriebsnachweise in dieser Recherche weniger breit sind.

**Mittel** bedeutet: dokumentierte und nutzbare Software mit noch begrenzter
Langzeiterfahrung, einer jungen Projektlinie oder größeren offenen Fragen zur
Integration. In jungen Unterkategorien lassen sich nicht seriös fünf Lösungen
mit sehr hohem Reifegrad belegen. Dort nennt die Auswahl die bevorzugten geprüften
Kandidaten und weist die geringere Reife ausdrücklich aus.

Innerhalb gleicher Reifegrade ist die Reihenfolge eine redaktionelle
Priorisierung für das Kapitel. Die Begründungen nennen die ausschlaggebenden
Merkmale; die Einordnungen zeigen Grenzen. Projektalter und GitHub-Sterne
allein bestimmen keinen Rang. Eine neuere Architekturgeneration bedeutet
nicht automatisch einen höheren Reifegrad.

## Umfang der Prüfung

Die Prüfung ist dokumentenbasiert. Es wurden keine Lasttests, Sicherheitsaudits
oder vergleichenden Installationen der aufgeführten Projekte durchgeführt. Die Auswahl
betrifft die Softwarekerne, nicht pauschal alle Plugins oder kommerziellen
Zusatzangebote. Mehrfachnennungen sind beabsichtigt: Ein Generator kann sowohl
Dokumente erstellen als auch Bestandteil eines Docs-as-Code-Prozesses sein.

Unterkategorien entsprechen den sieben Dokumentationsformen, sechs
Entwicklungsrichtungen der Wissenssysteme, fünf CMS-Richtungen plus dem
dateibasierten Parallelstrang, sechs Docs-as-Code-Richtungen, sechs Webframework-Richtungen plus den beiden ergänzenden Kategorien Batteries Included und Enterprise, sechs Lernmanagement-Entwicklungsstufen, fünf Mobile- und Desktop-App-Bereichen sowie acht Sprachmodell-Integrationsbereichen. Die
historischen Zeitabschnitte liefern die Gliederung; die Softwareauswahl
bezieht sich auf die gegenwärtigen Architekturprinzipien.

Bei KI und Agenten werden Anwendungen und Frameworks ausdrücklich
unterschieden. Ein reifer Baustein garantiert keine ausgereifte Gesamtplattform.
Die offene Lizenz eines Frameworks sagt außerdem nichts über die Lizenz
angeschlossener Sprachmodelle oder externer Dienste aus.

## Auswahlentscheidungen bei Projektänderungen

- **Pico** wird nicht aufgenommen: Das Projekt meldet sein Entwicklungsende
  und rät von neuen Websites ab. [Offizieller Projektstatus](https://github.com/picocms/Pico).
- **Logseq DB** wird für die auf Reife ausgerichtete Auswahl zurückgestellt:
  Die Projektdokumentation bezeichnet die DB-Version als Beta und RTC als Alpha.
  Das ist keine pauschale Bewertung aller früheren Logseq-Versionen.
  [Projektstatus](https://github.com/logseq/logseq).
- **mini-SWE-agent** ersetzt in der Auswahl SWE-agent entsprechend der
  Empfehlung des bisherigen Projekts. [Hinweis der Entwickler](https://github.com/SWE-agent/SWE-agent).
- **Microsoft Agent Framework** wird als Nachfolger von Semantic Kernel
  betrachtet und wegen der jungen Projektlinie vorsichtig bewertet.
  [Hinweis im Vorgängerprojekt](https://github.com/microsoft/semantic-kernel).
- **Strapi** wird nur in seiner offenen Community Edition aufgenommen.
  [Lizenz und Abgrenzung zum Enterprise-Code](https://github.com/strapi/strapi/blob/develop/LICENSE).

## Ergänzende Primärquellen

- [MediaWiki: Versionslebenszyklus](https://www.mediawiki.org/wiki/Version_lifecycle)
- [Drupal: Lizenz](https://www.drupal.org/about/licensing)
- [Sphinx: Lizenz](https://github.com/sphinx-doc/sphinx/blob/master/LICENSE.rst)
- [XWiki: Quellcode und Lizenz](https://github.com/xwiki/xwiki-platform)
- [TiddlyWiki: Lizenz](https://github.com/TiddlyWiki/TiddlyWiki5/blob/master/license)

Weitere Quellen stehen direkt bei den jeweiligen Einträgen.
Installationsanleitungen und ausführliche Praxisvergleiche können später folgen.

## Besonderheit bei Webframeworks

Bei Browser-Frameworks gilt die Auswahl für die ausdrücklich beschriebene
Kombination mit einem PostgreSQL-Backend. Es wird kein nativer Datenbankzugriff
des Frontends behauptet. Die [Speicherwege für Webframeworks](webframeworks.md#speicherwege-fuer-webframeworks)
erläutern die erforderliche Eigenentwicklung und die Grenzen der Prüfung.
