# Ajax und progressive Erweiterung

[Übergeordnete Kategorie: Webframeworks](../webframeworks.md)

Ajax ergänzt serverseitige Seiten um nachgeladene Inhalte. Die Auswahl umfasst etablierte Bibliotheken und heutige Fortführungen dieses Prinzips.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien in der beschriebenen Betriebsvariante.

Stand: **26. September 2026**. [Bewertungskriterien und Grenzen](../software.md).

| Rang | Software und offizielle Quelle | Lizenz des Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [jQuery](https://github.com/jquery/jquery) | MIT | Sehr hoch | Langjährig etablierte DOM- und Ajax-Bibliothek. | PostgreSQL über eigenes [Django-Backend](../webframeworks.md#speicherwege-fuer-webframeworks); [Frontend-Anbindung](https://jquery.com/) |
| 2 | [htmx](https://github.com/bigskysoftware/htmx) | 0BSD | Hoch | Dokumentierte HTML-Fragmente und servergesteuerte Interaktion. | PostgreSQL über eigenes [Django-Backend](../webframeworks.md#speicherwege-fuer-webframeworks); [Frontend-Anbindung](https://htmx.org/docs/) |
| 3 | [Stimulus](https://github.com/hotwired/stimulus) | MIT | Hoch | Schrittweise Interaktivität für vorhandene HTML-Seiten. | PostgreSQL über eigenes [Django-Backend](../webframeworks.md#speicherwege-fuer-webframeworks); [Frontend-Anbindung](https://stimulus.hotwired.dev/) |
| 4 | [Alpine.js](https://github.com/alpinejs/alpine) | MIT | Hoch | Kompakte deklarative Interaktion direkt im HTML. | PostgreSQL über eigenes [Django-Backend](../webframeworks.md#speicherwege-fuer-webframeworks); [Frontend-Anbindung](https://alpinejs.dev/) |
| 5 | [Unpoly](https://github.com/unpoly/unpoly) | MIT | Hoch | Dokumentierte Navigation und Formularverarbeitung mit HTML-Fragmenten. | PostgreSQL über eigenes [Django-Backend](../webframeworks.md#speicherwege-fuer-webframeworks); [Frontend-Anbindung](https://unpoly.com/) |

## Einsatz und Abgrenzung

Diese Bibliotheken sind keine Datenbanken. Aufgenommen wird jeweils die Kombination mit einem selbst entwickelten Django-Backend und PostgreSQL. HTML-Antworten und Formulare verbinden die Schichten; bei Alpine.js und Stimulus muss der HTTP-Zugriff selbst ergänzt werden.

Thematische Grundlage: [Evolution digitaler Webframeworks](https://dokument.wissen-ahrensburg.de/entwicklung/webentwicklung/evolution-digitaler-webframeworks/).
