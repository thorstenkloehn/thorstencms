# Softwareauswahl und Reifegrade

Die acht Hauptkategorien und 52 Unterkategorien enthalten eine redaktionelle
Auswahl von bis zu fünf Einträgen. Der Umfang richtet sich nach den belegbaren
Betriebsvarianten. Fehlende Kandidaten werden nicht durch ungesicherte Empfehlungen
ersetzt. Mehrfachnennungen sind beabsichtigt.

Die 60 Auswahltabellen enthalten zusammen **257 Einträge**.
Gezählt werden Tabellenzeilen einschließlich Mehrfachnennungen; eine Zahl
eindeutiger Projekte wird wegen kombinierter Einträge und Aliasnamen nicht behauptet.

Redaktioneller Stand: **27. September 2026**. Die Funktions- und Speicherquellen
stehen bei den Einträgen. Eine dokumentierte Möglichkeit ist kein Nachweis für
eine hier durchgeführte Installation oder einen aktuellen Vollvergleich aller Produkte.

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

### Betrachteter Umfang

Bei einer Anwendung umfasst der Filter die maßgeblichen Inhalte und den
Anwendungszustand der beschriebenen Variante. Ein nur rekonstruierbarer
Hilfsindex ist davon zu unterscheiden. Noch nicht synchronisierte Bearbeitungen
sind keine beliebig löschbaren Cache-Daten.

Bei mobilen LMS-Clients wird ausdrücklich nur der PostgreSQL-Serverbestand
bewertet. Diese Einträge sind keine Empfehlung für eine durchgehend SQLite-freie
Offline-Gesamtinstallation. Wer den Filter auch auf sämtliche Endgeräte anwenden
muss, kann aus diesen Client-Einträgen keine Eignung ableiten.

Bei Bibliotheken benennt die Tabelle den verwendeten Baustein und seinen
Speicherweg. Dateizugriff muss in der eigenen Anwendung implementiert werden.
Lokale Modelldateien einer Laufzeit sind keine Ablage für Dokumente oder Chats.
Externe Modellanbieter und zusätzliche Dienste benötigen eine eigene Prüfung.

**Sonderfall AnythingLLM:** Das Projekt beschreibt die Umstellung der
Anwendungsdatenbank auf PostgreSQL im
[Prisma-Schema](https://github.com/Mintplex-Labs/anything-llm/blob/master/server/prisma/schema.prisma).
Zusätzlich ist [pgvector](https://github.com/Mintplex-Labs/anything-llm/blob/master/server/utils/vectorDbProviders/pgvector/SETUP.md)
für Vektordaten einzurichten. Nur diese angepasste Variante bleibt enthalten;
ihre Reife wird wegen des Anpassungsbedarfs als mittel eingestuft.
Die Umstellung wurde hier nicht praktisch erprobt.

## Bewertungsmethode

Die Auswahl ist eine redaktionelle Empfehlung aus den geprüften Projekten,
kein vollständiger Marktvergleich. Die Reifegrade sind qualitative Urteile,
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
Integration. Eine komplexe oder noch wenig erprobte Betriebsvariante wird entsprechend
vorsichtig eingeordnet. Kategorien dürfen weniger als fünf Einträge enthalten.

Die Reife bewertet den benannten Kern beziehungsweise die ausdrücklich genannte
Betriebsvariante. Bei LMS-Anbindungen wird die Reife des LMS-Kerns angegeben,
nicht die eines beliebigen KI-Tutors. Drupal AI wird separat mit „Mittel“
eingeordnet. LangChain, LlamaIndex und SiYuan werden in ihren wiederholten
Nennungen einheitlich mit „Hoch“ bewertet. Abweichungen benötigen eine Erklärung.

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

Die 52 Unterkategorien gliedern sich in sieben Dokumentationsformen, sechs
Wissenssystem-Bereiche, sechs CMS-Bereiche, sechs Docs-as-Code-Bereiche, acht
Webframework-Bereiche, sechs LMS-Bereiche, fünf App-Bereiche und acht Bereiche
der Sprachmodellanbindung. Diese Arbeits- und Architekturformen überschneiden
sich; sie sind kein verbindliches historisches Generationenmodell.

Bei KI und Agenten werden Anwendungen und Frameworks ausdrücklich
unterschieden. Ein reifer Baustein garantiert keine ausgereifte Gesamtplattform.
Die offene Lizenz eines Frameworks sagt außerdem nichts über die Lizenz
angeschlossener Sprachmodelle oder externer Dienste aus.

## Zurueckgestellte Projekte

Die folgenden Entscheidungen beziehen sich auf den engen Filter dieses Buches.
Sie sind keine pauschale Bewertung der Qualität der jeweiligen Software.

| Projekt | Grund für die Nichtaufnahme beziehungsweise weitere Prüfung |
| --- | --- |
| Open edX und sein mobiler Client | [OEP-67](https://docs.openedx.org/projects/openedx-proposals/en/latest/best-practices/oep-0067-bp-tools-and-technology.html) nennt MySQL als einzig offiziell unterstütztes Django-ORM-Backend. Die frühere PostgreSQL-Zusage wurde entfernt. |
| Joplin | Laut [Architekturdokumentation](https://joplinapp.org/help/dev/spec/architecture/) liegen auch Notizen in SQLite. Ein Markdown-Export ändert den Hauptspeicher nicht. |
| Directus | Der am Prüftag abgerufene [main-Stand der Lizenz](https://github.com/directus/directus/blob/main/license) verwendet MSCL-1.0-GPL mit Nutzungsbeschränkungen und späterem GPL-Übergang. Eine versionslose GPL-3.0-Angabe ist damit nicht ausreichend. |
| Dify | Die [Lizenz](https://github.com/langgenius/dify/blob/main/LICENSE) ergänzt Apache 2.0 um zusätzliche Bedingungen. Die frühere uneingeschränkte Apache-2.0-Angabe wurde entfernt. |
| Kolibri | Die [Datenbankkonfiguration](https://github.com/learningequality/kolibri/blob/develop/kolibri/deployment/default/settings/base.py) enthält SQLite- und PostgreSQL-Wege. Ein durchgehend passender Betrieb aller Inhalts- und Benutzerdaten wurde hier nicht belegt; Inhaltskanäle allein genügen nicht. |
| Sakai | Die [Administrationsdokumentation](https://sakaiproject.atlassian.net/wiki/spaces/DOC/pages/17225318567/Sakai+Admin+Guide+-+Full) beschreibt MySQL und Oracle. Für die behauptete PostgreSQL-Variante fehlt hier ein tragfähiger Nachweis. |
| Frappe LMS | Die geprüfte [Compose-Konfiguration](https://github.com/frappe/lms/blob/develop/docker/docker-compose.yml) verwendet MariaDB. PostgreSQL-Unterstützung des Frappe-Frameworks belegt nicht die Eignung der LMS-Anwendung. |
| WordPress Mobile und Ghost Desktop | Die bisher genannten Cache- und API-Funktionen belegten keinen erlaubten Hauptspeicher des vollständigen Systems. |
| WatermelonDB, PouchDB und RxDB | Die bisher genannten lokalen Datenbanken und Replikationswege belegten keine vollständige Variante nach dem hier verwendeten Datei-/PostgreSQL-Filter. |
| Opigno LMS, Ralph LRS und TRAX LRS | Die bisherigen Verweise belegten die konkret behaupteten PostgreSQL-Gesamtvarianten nicht ausreichend. Ein Framework- oder Projektlink allein reicht nicht. |
| RAGFlow | Die [Betriebskonfiguration](https://github.com/infiniflow/ragflow/blob/main/docker/docker-compose-base.yml) enthält verschiedene Dienste und Speicherprofile. Ein PostgreSQL-Metadatenspeicher allein belegt nicht die Einhaltung des Filters für alle benötigten Daten. |
| BigBlueButton und mobile Browsernutzung | Aufzeichnungsdateien allein belegen nicht den gesamten Speicherbedarf der Konferenzplattform. Eine entsprechende Gesamtkonfiguration ist hier nicht nachgewiesen. |
| Logseq | Datei- und Datenbanklinien müssen versionsgenau unterschieden werden. Der bisherige Link auf das Gesamtprojekt genügte nicht als Nachweis einer ausgewählten gepflegten Dateivariante. |
| React Native | Die bisher pauschal genannten offiziellen SQLite-/Dateimodule waren kein konkreter Nachweis für die gewählte Dateianbindung. |

Auch nicht aufgeführte Produkte können geeignet sein. Eine spätere Aufnahme
benötigt eine eindeutig benannte Version oder Betriebsvariante mit Funktions-,
Lizenz- und Speichernachweis. Verweise auf bewegliche Zweige wie `main` oder
`develop` sind Recherchebelege zum Prüftag und keine Zusage für spätere Releases.

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
