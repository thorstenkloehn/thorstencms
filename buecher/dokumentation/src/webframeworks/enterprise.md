# Enterprise-Webframeworks

[Übergeordnete Kategorie: Webframeworks](../webframeworks.md)

Enterprise-Webframeworks unterstützen langfristig gepflegte Geschäftsanwendungen mit geregelten Zugriffsrechten, Datenzugriff, Schnittstellen und Betriebsprozessen. Ausschlaggebend sind Dokumentation, Wartbarkeit und ein tragfähiges Ökosystem; die Programmiersprache allein entscheidet nicht über die Eignung.

Diese Kategorie betrachtet den Einsatz in Organisationen. Sie überschneidet sich bewusst mit Batteries-Included- und serverseitigen Frameworks. „Enterprise“ ist hier eine redaktionelle Einordnung, keine Zertifizierung.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**. [Bewertungskriterien und Grenzen](../software.md).
Die Rangfolge ordnet bewährte Enterprise-Stacks nach Betriebssicherheit und Ökosystem-Reife.

| Rang | Software und offizielle Quelle | Lizenz des Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Spring Boot](https://github.com/spring-projects/spring-boot) | Apache-2.0 | Sehr hoch | Umfangreiche Betriebs- und Datenzugriffsdokumentation für Java-Anwendungen. | PostgreSQL: [DataSource mit PostgreSQL-JDBC-Treiber konfigurieren](https://docs.spring.io/spring-boot/how-to/data-access.html) |
| 2 | [ASP.NET Core](https://github.com/dotnet/aspnetcore) | MIT | Sehr hoch | Etabliertes plattformübergreifendes .NET-Framework für MVC, Razor Pages und HTTP-APIs. | PostgreSQL: [EF Core mit Npgsql und UseNpgsql konfigurieren](https://www.npgsql.org/efcore/) |
| 3 | [Django](https://github.com/django/django) | BSD-3-Clause | Sehr hoch | Langjähriges Python-Framework mit ORM, Admin und umfassendem Handbuch. | PostgreSQL: [Offizielles Datenbank-Backend](https://docs.djangoproject.com/en/stable/ref/databases/#postgresql-notes) |
| 4 | [Symfony](https://github.com/symfony/symfony) | MIT | Sehr hoch | Langjähriger PHP-Unterbau mit wiederverwendbaren Komponenten. | PostgreSQL: [Doctrine und PostgreSQL-Verbindungsadresse](https://symfony.com/doc/current/doctrine.html) |
| 5 | [Ruby on Rails](https://github.com/rails/rails) | MIT | Sehr hoch | Etabliertes MVC-System mit Migrationen und integriertem Anwendungsmodell. | PostgreSQL: [Active-Record-Konfiguration](https://guides.rubyonrails.org/configuring.html#configuring-a-postgresql-database) |

## Funktionsumfang und Einordnung

- **Spring Boot:** Java-Anwendungen mit konfigurierbarem Datenzugriff und Betriebsfunktionen über Actuator. PostgreSQL wird über den JDBC-Treiber angebunden; benötigte Sicherheitsmodule müssen eingerichtet werden. [Offizielle Dokumentation](https://docs.spring.io/spring-boot/reference/actuator/index.html).

- **ASP.NET Core:** Plattformübergreifender .NET-Unterbau für Weboberflächen und APIs. EF Core mit Npgsql ermöglicht PostgreSQL; SQL Server ist dafür nicht erforderlich. [Offizielle Dokumentation](https://www.npgsql.org/efcore/).

- **Django:** Geeignet für datenorientierte Geschäftsanwendungen mit integrierter Benutzerverwaltung und Admin. Fachliche Rollen und organisationsweite Anmeldung benötigen projektspezifische Ausgestaltung. [Offizielle Dokumentation](https://docs.djangoproject.com/en/stable/).

- **Symfony:** Komponentenorientierter PHP-Unterbau für langfristig entwickelte Anwendungen. Datenmodelle und Migrationen können mit Doctrine umgesetzt werden. [Offizielle Dokumentation](https://symfony.com/doc/current/doctrine.html).

- **Ruby on Rails:** Konventionsorientierter Full-Stack-Unterbau für Geschäftsanwendungen. Fachliche Berechtigungen und Betriebsabläufe bleiben Aufgaben des Entwicklungsteams. [Offizielle Dokumentation](https://guides.rubyonrails.org/).

## Betriebsvariante

Im Enterprise-Umfeld erfordert der PostgreSQL-Betrieb eine sorgfältige Dimensionierung von Verbindungspools (z. B. via PgBouncer), Replikation und Mandantentrennung. Zusätzliche Datenbanken für Metadaten sind ausgeschlossen; alle persistenten Geschäftsdaten verbleiben gemäß [Speicherfilter](../software.md#verbindlicher-speicherfilter) in PostgreSQL. Diese Architekturen wurden für dieses Buch nicht praktisch aufgebaut.
