# Serverseitige Frameworks: CGI, MVC und Enterprise

[Übergeordnete Kategorie: Webframeworks](../webframeworks.md)

Serverseitige Frameworks verbinden Anfragen, Geschäftslogik, Datenzugriff und HTML-Ausgabe. Die Auswahl betrachtet heutige Frameworks mit serverseitiger Anwendungslogik. Historische CGI-Werkzeuge sind nicht Gegenstand dieser Produktauswahl.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**. [Bewertungskriterien und Grenzen](../software.md).

| Rang | Software und offizielle Quelle | Lizenz des Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Django](https://github.com/django/django) | BSD-3-Clause | Sehr hoch | Langjähriges Python-Framework mit ORM, Admin und umfassendem Handbuch. | PostgreSQL: [Offizielles Datenbank-Backend](https://docs.djangoproject.com/en/stable/ref/databases/#postgresql-notes) |
| 2 | [Ruby on Rails](https://github.com/rails/rails) | MIT | Sehr hoch | Etabliertes MVC-System mit Migrationen und integriertem Anwendungsmodell. | PostgreSQL: [Active-Record-Konfiguration](https://guides.rubyonrails.org/configuring.html#configuring-a-postgresql-database) |
| 3 | [Spring Boot](https://github.com/spring-projects/spring-boot) | Apache-2.0 | Sehr hoch | Umfangreiche Betriebs- und Datenzugriffsdokumentation für Java-Anwendungen. | PostgreSQL: [DataSource mit PostgreSQL-JDBC-Treiber konfigurieren](https://docs.spring.io/spring-boot/how-to/data-access.html) |
| 4 | [Symfony](https://github.com/symfony/symfony) | MIT | Sehr hoch | Langjähriger PHP-Unterbau mit wiederverwendbaren Komponenten. | PostgreSQL: [Doctrine und PostgreSQL-Verbindungsadresse](https://symfony.com/doc/current/doctrine.html) |
| 5 | [ASP.NET Core](https://github.com/dotnet/aspnetcore) | MIT | Sehr hoch | Etabliertes plattformübergreifendes .NET-Framework für MVC, Razor Pages und HTTP-APIs. | PostgreSQL: [EF Core mit Npgsql und UseNpgsql konfigurieren](https://www.npgsql.org/efcore/) |

## Einsatz und Abgrenzung

Alle fünf Projekte benötigen eine selbst entwickelte Anwendung. PostgreSQL muss als Datenbank gewählt werden; zusätzliche Queue-, Cache- und Session-Dienste dürfen den Speicherfilter nicht umgehen.

**Architektur von ASP.NET Core:** Basiert auf der modularen Kestrel-Webserver-Pipeline und Entity Framework Core. Die relationale Anbindung an PostgreSQL wird über den Treiber `Npgsql.EntityFrameworkCore.PostgreSQL` (`UseNpgsql`) realisiert, wodurch die Lösung vollständig ohne Microsoft SQL Server betrieben werden kann. Razor Pages und Controller ermöglichen klassische serverseitige Render-Workflows.
