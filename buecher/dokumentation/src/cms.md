# Content-Management-Systeme: Redaktion und Auslieferung

Ein CMS verwaltet Inhalte, die mehrere Menschen erstellen, prüfen und
veröffentlichen. Für die Auswahl ist etwa entscheidend, ob eine Redaktion
fertige Seiten bearbeitet oder strukturierte Angaben wie Titel, Termin,
Veranstaltungsort und Anmeldelink pflegt.

## Beispiel: Eine Veranstaltung auf mehreren Kanälen

Eine Redaktion erfasst die Veranstaltung einmal. Die Website zeigt einen
langen Beschreibungstext, eine App zunächst nur Termin und Ort. Wird die
Veranstaltung abgesagt, muss die Änderung auf beiden Kanälen ankommen.
Dafür werden ein gemeinsames Inhaltsmodell, Zuständigkeiten und Regeln für
Zwischenspeicher benötigt. Eine API allein erledigt diese Abstimmung nicht.

## Wie die Bausteine zusammenarbeiten

Bei einem integrierten CMS gehören Inhaltspflege und Seitenausgabe zur selben
Anwendung. Bei einer entkoppelten Lösung übernimmt ein eigenes Frontend die
Darstellung. Das schafft Gestaltungsspielraum, bringt aber zusätzliche Arbeit
für Vorschau, Anmeldung und Veröffentlichung mit sich.

Dateibasierte Systeme passen zu Beständen, die sich gut als Text und Medien
verwalten lassen. Relationale Inhaltsmodelle können dagegen eine Datenbank
nahelegen. In dieser Auswahl werden PostgreSQL und direkte Inhaltsdateien
betrachtet. Das ist eine redaktionelle Eingrenzung, keine allgemeine Aussage
über die Qualität anderer Datenbanken.

KI-Erweiterungen können Entwürfe oder Metadaten vorschlagen. Die Reife eines
CMS-Kerns belegt dabei weder die Qualität einer Erweiterung noch die Richtigkeit
ihrer Ausgaben. Automatische Veröffentlichung benötigt eigene Prüfregeln.

## Unterkategorien: gefilterte Softwareauswahl

- [Klassische CMS](cms/klassisch.md)
- [Headless und Decoupled CMS](cms/headless.md)
- [Composable CMS](cms/composable.md)
- [KI-gestützte Content-Erstellung](cms/ki-content.md)
- [Agentische Abläufe](cms/agentisch.md)
- [Git-basierte und Flat-File-CMS](cms/dateibasiert.md)

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: 27. September 2026. Auswahl nach der
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
