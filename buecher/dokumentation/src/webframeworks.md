# Evolution digitaler Webframeworks

Webframeworks bilden die technische Grundlage für Webanwendungen, Inhaltsportale und interaktive Wissenssysteme. Das Kapitel ergänzt die bisherigen Perspektiven um Darstellung, Anwendungslogik und Datenzugriff.

Die Ausgangsseite unterscheidet sechs Entwicklungsrichtungen. Diese überlappen: Eine aktuelle Anwendung kann serverseitige Logik, interaktive Komponenten und KI-Funktionen kombinieren. Das Generationenmodell ist eine Orientierung, keine Reifegradskala.

## Unterkategorien

- [Serverseitige Frameworks: CGI, MVC und Enterprise](webframeworks/serverseitig.md)
- [Ajax und progressive Erweiterung](webframeworks/ajax.md)
- [Single-Page-Applications](webframeworks/spa.md)
- [Full-Stack- und Meta-Frameworks](webframeworks/meta-frameworks.md)
- [Server Components, Islands und Edge](webframeworks/islands-edge.md)
- [KI-native Bausteine und agentengestützte Entwicklung](webframeworks/ki-agenten.md)

### Ergänzende Kategorien nach Funktionsumfang und Einsatz

- [Batteries-Included-Webframeworks](webframeworks/batteries-included.md)
- [Enterprise-Webframeworks](webframeworks/enterprise.md)

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien in der beschriebenen Betriebsvariante.

Stand: **26. September 2026**. [Bewertungskriterien und Grenzen](software.md).

| Rang | Software und offizielle Quelle | Lizenz des Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Django](https://github.com/django/django) | BSD-3-Clause | Sehr hoch | Langjähriges Python-Framework mit ORM, Admin und umfassendem Handbuch. | PostgreSQL: [Offizielles Datenbank-Backend](https://docs.djangoproject.com/en/stable/ref/databases/#postgresql-notes) |
| 2 | [Ruby on Rails](https://github.com/rails/rails) | MIT | Sehr hoch | Etabliertes MVC-System mit Migrationen und integriertem Anwendungsmodell. | PostgreSQL: [Active-Record-Konfiguration](https://guides.rubyonrails.org/configuring.html#configuring-a-postgresql-database) |
| 3 | [Spring Boot](https://github.com/spring-projects/spring-boot) | Apache-2.0 | Sehr hoch | Umfangreiche Betriebs- und Datenzugriffsdokumentation für Java-Anwendungen. | PostgreSQL: [DataSource mit PostgreSQL-JDBC-Treiber konfigurieren](https://docs.spring.io/spring-boot/how-to/data-access.html) |
| 4 | [Symfony](https://github.com/symfony/symfony) | MIT | Sehr hoch | Langjähriger PHP-Unterbau mit wiederverwendbaren Komponenten. | PostgreSQL: [Doctrine und PostgreSQL-Verbindungsadresse](https://symfony.com/doc/current/doctrine.html) |
| 5 | [ASP.NET Core](https://github.com/dotnet/aspnetcore) | MIT | Sehr hoch | Etabliertes plattformübergreifendes .NET-Framework für MVC, Razor Pages und HTTP-APIs. | PostgreSQL: [EF Core mit Npgsql und UseNpgsql konfigurieren](https://www.npgsql.org/efcore/) |

## Speicherwege fuer Webframeworks

Ein Framework liefert Bausteine für eine Anwendung. Die hier ausgewählte
Betriebsvariante muss beim Entwickeln ausdrücklich umgesetzt werden.

- **Server-Frameworks:** PostgreSQL über das dokumentierte ORM oder den Datenbanktreiber konfigurieren.
- **Browser-Bibliotheken und SPAs:** Die Auswahl gilt ausschließlich zusammen mit einem eigenen Django-Backend, dessen Datenbank PostgreSQL ist. Für JSON-Schnittstellen ergänzt [Django REST framework](https://www.django-rest-framework.org/) das Backend. Browser greifen per HTTP darauf zu, niemals mit Datenbankzugangsdaten direkt auf PostgreSQL. Diese Kombination ist eine redaktionell abgeleitete Architektur, keine Herstellerzertifizierung.
- **Node.js- und Deno-Frameworks:** PostgreSQL-Treiber gehören in serverseitige Routen. Hosting, Verbindungsverwaltung und Migrationen müssen passend eingerichtet werden.
- **Inhaltsdateien:** Markdown und MDX sind maßgebliche Inhalte; Quellcode-Dateien allein machen ein beliebiges Framework noch nicht zu einem dateibasierten Wissenssystem.

Die [Django-Dokumentation](https://docs.djangoproject.com/en/stable/ref/databases/#postgresql-notes)
belegt den PostgreSQL-Speicherweg des gemeinsamen Beispiel-Backends.
Keine dieser Kombinationen wurde für dieses Buch installiert oder im Zusammenspiel getestet.

## Architekturfragen

Rendering und Speicherung sind unabhängige Entscheidungen. Statische Ausgabe
passt zu selten veränderten Inhalten. Individuelle Benutzeraktionen benötigen
serverseitige Verarbeitung und dauerhafte Speicherung. Islands reduzieren den
interaktiven Anteil einer Seite; Edge-Betrieb beschreibt den Ausführungsort.
KI-Werkzeuge können die Entwicklung unterstützen, ersetzen aber weder diese
Entscheidungen noch die fachliche Prüfung.

Quelle: [Evolution und Architekturen digitaler Web-Frameworks](https://dokument.wissen-ahrensburg.de/entwicklung/webentwicklung/evolution-digitaler-webframeworks/).

**Einordnung von ASP.NET Core:** Serverseitiges Framework der Enterprise-Linie.
Die Auswahl verwendet PostgreSQL über Npgsql; SQL Server ist dafür nicht erforderlich.
ASP.NET Core ersetzt hier Laravel, damit die Liste bei fünf Projekten bleibt und
neben Python, Ruby, Java und PHP auch .NET abdeckt. Das ist eine Entscheidung
für die Breite der Auswahl, keine pauschale Abwertung von Laravel.
