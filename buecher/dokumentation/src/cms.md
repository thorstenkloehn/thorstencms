# Evolution digitaler Content-Management-Systeme

Content-Management-Systeme organisieren die Erstellung, Pflege und Auslieferung
von Inhalten. Die Ausgangsseite gliedert ihre Entwicklung nach Architektur:

| Richtung | Prinzip |
| --- | --- |
| Klassische CMS | Redaktion, Speicherung und Seitenausgabe sind eng verbunden |
| Headless und Decoupled CMS | Inhaltspflege und Darstellung werden getrennt; Schnittstellen verbinden sie |
| Composable CMS | Mehrere spezialisierte Dienste bilden gemeinsam die Publikationsumgebung |
| KI-gestützte Systeme | Assistenz unterstützt Texterstellung und Personalisierung |
| Agentische Systeme | Agenten übernehmen mehrstufige Aufgaben in der Inhaltspflege |

Git-basierte und Flat-File-Ansätze bilden einen ergänzenden Entwicklungsstrang.
Speicherarchitektur und Auslieferungsmodell sind dabei getrennte Fragen:
Dateispeicherung allein beschreibt noch keinen vollständigen Redaktionsprozess.

## Unterkategorien: gefilterte Softwareauswahl

- [Klassische CMS](cms/klassisch.md)
- [Headless und Decoupled CMS](cms/headless.md)
- [Composable CMS](cms/composable.md)
- [KI-gestützte Content-Erstellung](cms/ki-content.md)
- [Agentische Content-Systeme](cms/agentisch.md)
- [Git-basierte und Flat-File-CMS](cms/dateibasiert.md)

## Geplante Vertiefung

- Inhalt, Darstellung und Auslieferung
- Redaktionelle Rollen und Freigaben
- Schnittstellen und Wiederverwendung über mehrere Kanäle

Quelle: [Evolution und Architekturen digitaler Content-Management-Systeme](https://dokument.wissen-ahrensburg.de/wissen/dokumentation/evolution-digitaler-cms/).

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: 26. September 2026. Redaktionelle Auswahl nach der
[gemeinsamen Bewertungsmethode](software.md). Die Reihenfolge priorisiert
Reife und anschließend die Eignung für diese Kategorie.

| Rang | Software | Lizenz des Kerns | Reifegrad | Schwerpunkt | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Drupal](https://www.drupal.org/project/drupal/releases) | GPL-2.0-or-later | Sehr hoch | Strukturierte Inhaltsportale | PostgreSQL: [PostgreSQL](https://www.drupal.org/docs/getting-started/system-requirements/database-server-requirements) |
| 2 | [TYPO3](https://github.com/TYPO3/typo3) | GPL-2.0-or-later | Sehr hoch | Umfangreiche redaktionelle Webauftritte | PostgreSQL: [PostgreSQL](https://docs.typo3.org/m/typo3/reference-coreapi/main/en-us/Administration/Installation/SystemRequirements/Index.html) |
| 3 | [Joomla](https://github.com/joomla/joomla-cms) | GPL-2.0-or-later | Sehr hoch | Allgemeine Inhalts- und Community-Websites | PostgreSQL: [PostgreSQL](https://manual.joomla.org/docs/next/get-started/technical-requirements/) |
| 4 | [Wagtail](https://github.com/wagtail/wagtail) | BSD-3-Clause | Hoch | Individuelle CMS-Projekte auf Django | PostgreSQL: [PostgreSQL](https://docs.wagtail.org/en/stable-7.4.x/releases/upgrading.html) |
| 5 | [Grav](https://github.com/getgrav/grav) | MIT | Hoch | Dateibasierte Websites und schlanke Inhaltsportale | Dateien: [Markdown-, YAML- und Mediendateien](https://github.com/getgrav/grav) |

### 1. Drupal

**Begründung:** Dokumentierte produktionsgeeignete Core-Releases und ein geregelter Veröffentlichungsprozess.

**Einordnung:** Modulabhängigkeiten und größere Upgrades benötigen Planung.

Offizielle Grundlage: [Drupal](https://www.drupal.org/project/drupal/releases).

### 2. TYPO3

**Begründung:** Etablierte CMS-Plattform mit eigenem Core-Team, Community und Betriebsdokumentation.

**Einordnung:** Einrichtung und projektspezifische Anpassungen verlangen Fachkenntnisse.

Offizielle Grundlage: [TYPO3](https://github.com/TYPO3/typo3).

### 3. Joomla

**Begründung:** Langjähriges CMS mit Versionshistorie, technischen Anforderungen und dokumentiertem Entwicklungsprozess.

**Einordnung:** Erweiterungen müssen zur eingesetzten Hauptversion passen.

Offizielle Grundlage: [Joomla](https://github.com/joomla/joomla-cms).

### 4. Wagtail

**Begründung:** Dokumentiertes CMS mit Community, kommerziellem Support und offenem Änderungsverlauf.

**Einordnung:** Benötigt für individuelle Inhaltsmodelle ein Django-Entwicklungsteam.

Offizielle Grundlage: [Wagtail](https://github.com/wagtail/wagtail).

### 5. Grav

**Begründung:** Dokumentiertes PHP-System mit Markdown und Templates.

**Einordnung:** Ergänzt die klassischen redaktionellen CMS um eine dateibasierte Variante mit Admin-Oberfläche. Inhalte liegen in Markdown und YAML; relationale Inhaltsmodelle sind nicht sein Schwerpunkt.

Offizielle Grundlage: [Grav](https://github.com/getgrav/grav).

