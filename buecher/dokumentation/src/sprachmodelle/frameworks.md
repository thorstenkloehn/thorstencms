# Sprachmodelle in Webframeworks & Backend

[Übergeordnete Kategorie: Integration von Sprachmodellen in Software-Architekturen](../sprachmodell-integration.md)

Modellanbindung auf Service- und Controller-Ebene, Token-Streaming (SSE), Function Calling und Datenbankspeicherung.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Spring Boot](https://github.com/spring-projects/spring-boot) / [Spring AI](https://github.com/spring-projects/spring-ai) | Apache-2.0 | Sehr hoch | Ausgereifte Java-Abstraktion für Chat-Clients, Prompt-Templates und pgvector-Stores. | PostgreSQL: [pgvector-Integration via Spring AI](https://docs.spring.io/spring-ai/reference/api/vectordbs/pgvector.html) |
| 2 | [ASP.NET Core](https://github.com/dotnet/aspnetcore) / [Semantic Kernel](https://github.com/microsoft/semantic-kernel) | MIT | Sehr hoch | Plattformübergreifender .NET-Stack für KI-Agenten, Plugins und Npgsql-PostgreSQL. | PostgreSQL: [EF Core mit Npgsql- und pgvector-Anbindung](https://www.npgsql.org/efcore/) |
| 3 | [Django](https://github.com/django/django) | BSD-3-Clause | Sehr hoch | Etabliertes Python-Webframework für datengetriebene KI-Services mit ORM und pgvector. | PostgreSQL: [Offizielles PostgreSQL-Backend](https://docs.djangoproject.com/en/stable/ref/databases/#postgresql-notes) |
| 4 | [FastAPI](https://github.com/fastapi/fastapi) | MIT | Sehr hoch | Asynchrones Python-API-Framework für latenzarmes Token-Streaming und Modell-Gateways. | PostgreSQL: [AsyncPG und SQLAlchemy mit PostgreSQL](https://fastapi.tiangolo.com/) |
| 5 | [Symfony](https://github.com/symfony/symfony) | MIT | Sehr hoch | Modulares PHP-Framework mit LLM-Integrations-Bundles und Doctrine-PostgreSQL. | PostgreSQL: [Doctrine und PostgreSQL-Anbindung](https://symfony.com/doc/current/doctrine.html) |

## Einsatz und Abgrenzung

Webframeworks kapseln Modell-APIs und schützen interne Systeme durch Validierung und Authentifizierung.

- **Spring AI:** Ideal für strukturierte Unternehmensanwendungen; erfordert Java-Laufzeitumgebung.
- **ASP.NET Core / Semantic Kernel:** Hohe Typsicherheit und Performance; erfordert .NET-Kenntnisse.
- **Django:** Verbindet bewährte Benutzerverwaltung mit Python-KI-Ökosystemen; synchrone Views durch Celery für LLMs entkoppeln.
- **FastAPI:** Hervorragend für Streaming-Endpunkte (SSE); erfordert für komplexe Geschäftslogik eigene Architekturmuster.
- **Symfony:** Robuste Basis für PHP-Entwickler; Token-Streaming setzt asynchrone Worker oder Messenger voraus.
