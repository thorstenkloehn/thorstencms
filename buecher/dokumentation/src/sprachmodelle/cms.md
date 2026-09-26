# Sprachmodelle in Content-Management-Systemen

[Übergeordnete Kategorie](../sprachmodell-integration.md)

Betrachtet wird eine dokumentierte KI-Erweiterung. Die Reife des CMS-Kerns wird nicht auf die Erweiterung übertragen.

## Open-Source-Auswahl nach Reifegrad

**1 Eintrag:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**. [Bewertungskriterien und Grenzen](../software.md).

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Drupal AI](https://www.drupal.org/project/ai) | GPL-2.0-or-later | Mittel | Offizielle Drupal-Projektseite mit Releases und Dokumentation. | PostgreSQL: [PostgreSQL über Drupal; externe KI-Speicher separat konfigurieren](https://www.drupal.org/docs/getting-started/system-requirements/database-server-requirements) |

## Einsatz und Abgrenzung

Drupal AI stellt eine Anbindung für Modellanbieter und KI-Funktionen bereit.
Welche Funktionen nutzbar sind, hängt von installierten Modulen und der
Konfiguration ab. Dokumentierte Ausgangspunkte sind die
[Moduldokumentation](https://www.drupal.org/docs/extending-drupal/contributed-modules/contributed-module-documentation/ai)
und die [Projektseite](https://www.drupal.org/project/ai).

Für die gewählte Variante liegen die Drupal-Inhalte in PostgreSQL. Ein externer
Vektorspeicher wird dadurch nicht automatisch umgestellt. Modellanbieter,
zusätzliche Speicherung und Freigaben sind ausdrücklich einzurichten.

Beispiel: Eine Redaktion lässt einen Beschreibungstext vorschlagen, prüft ihn
und speichert erst die angenommene Fassung. Die Veröffentlichung bleibt ein
separater Schritt. Für andere CMS werden hier keine unbenannten KI-Plugins
als nachgewiesene Produkteigenschaft ausgegeben.
