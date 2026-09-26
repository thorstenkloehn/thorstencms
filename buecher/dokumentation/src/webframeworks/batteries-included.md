# Batteries-Included-Webframeworks

[Übergeordnete Kategorie: Webframeworks](../webframeworks.md)

Batteries Included bezeichnet Frameworks, die viele wiederkehrende Aufgaben einer Webanwendung abdecken: Routing, Darstellung, Formulare, Validierung, Authentifizierung und Datenzugriff. Der Umfang unterscheidet sich. Einige Funktionen gehören zum Kern, andere werden durch offiziell gepflegte Pakete ergänzt.

Diese Kategorie beschreibt den Funktionsumfang und ergänzt die sechs Entwicklungsrichtungen. Sie ist keine zusätzliche historische Generation.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**. [Bewertungskriterien und Grenzen](../software.md).
Die Rangfolge gewichtet den Umfang integrierter Standardwerkzeuge und deren Reifegrad.

| Rang | Software und offizielle Quelle | Lizenz des Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Django](https://github.com/django/django) | BSD-3-Clause | Sehr hoch | Langjähriges Python-Framework mit ORM, Admin und umfassendem Handbuch. | PostgreSQL: [Offizielles Datenbank-Backend](https://docs.djangoproject.com/en/stable/ref/databases/#postgresql-notes) |
| 2 | [Ruby on Rails](https://github.com/rails/rails) | MIT | Sehr hoch | Etabliertes MVC-System mit Migrationen und integriertem Anwendungsmodell. | PostgreSQL: [Active-Record-Konfiguration](https://guides.rubyonrails.org/configuring.html#configuring-a-postgresql-database) |
| 3 | [Laravel](https://github.com/laravel/framework) | MIT | Sehr hoch | Integriertes PHP-Ökosystem mit Eloquent, Migrationen, Validierung und Authentifizierungsbausteinen. | PostgreSQL: [Offiziell unterstütztes Datenbank-Backend](https://laravel.com/docs/12.x/database) |
| 4 | [ASP.NET Core](https://github.com/dotnet/aspnetcore) | MIT | Sehr hoch | Etabliertes plattformübergreifendes .NET-Framework für MVC, Razor Pages und HTTP-APIs. | PostgreSQL: [EF Core mit Npgsql und UseNpgsql konfigurieren](https://www.npgsql.org/efcore/) |
| 5 | [Symfony](https://github.com/symfony/symfony) | MIT | Sehr hoch | Langjähriger PHP-Unterbau mit wiederverwendbaren Komponenten. | PostgreSQL: [Doctrine und PostgreSQL-Verbindungsadresse](https://symfony.com/doc/current/doctrine.html) |

## Funktionsumfang und Einordnung

- **Django:** ORM, Migrationen, Formulare, Authentifizierung und Admin-Oberfläche bilden ein eng integriertes Gesamtpaket. [Offizielle Dokumentation](https://docs.djangoproject.com/en/stable/).

- **Ruby on Rails:** Konventionen verbinden MVC, Active Record, Migrationen und weitere Anwendungsfunktionen. Eine allgemeine Admin-Oberfläche gehört nicht automatisch dazu. [Offizielle Dokumentation](https://guides.rubyonrails.org/).

- **Laravel:** Eloquent, Blade, Validierung und Authentifizierungsbausteine unterstützen vollständige Anwendungen. Starter-Kits und Zusatzpakete sind gesondert auszuwählen. [Offizielle Dokumentation](https://laravel.com/docs/12.x).

- **ASP.NET Core:** MVC, Razor Pages, Dependency Injection und Authentifizierungsbausteine sind verfügbar. Für PostgreSQL kommen EF Core und der Npgsql-Provider hinzu; eine allgemeine Admin-Oberfläche ist nicht enthalten. [Offizielle Dokumentation](https://learn.microsoft.com/en-us/aspnet/core/overview).

- **Symfony:** Für diese Auswahl gilt die vollständige Webanwendung mit den passenden Symfony-Paketen sowie Doctrine. Eine minimale Symfony-Installation enthält nicht automatisch alle Funktionen. [Offizielle Dokumentation](https://symfony.com/doc/current/setup.html).

## Betriebsvariante

Für Batteries-Included-Frameworks müssen alle integrierten Subsysteme wie Sitzungsverwaltung, Cache-Adapter und asynchrone Warteschlangen so konfiguriert werden, dass sie den [Speicherfilter](../software.md#verbindlicher-speicherfilter) einhalten (beispielsweise relationale Datenbank-Backends für Queues statt externer Key-Value-Speicher). Die beschriebenen Setups wurden für dieses Buch nicht installiert oder getestet.
