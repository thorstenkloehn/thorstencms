# Sprachmodelle in Webframeworks & Backend

[Übergeordnete Kategorie: Integration von Sprachmodellen in Software-Architekturen](../sprachmodell-integration.md)

Modellanbindung auf Service- und Controller-Ebene, Token-Streaming (SSE), Function Calling und Datenbankspeicherung.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [ASP.NET Core](https://github.com/dotnet/aspnetcore) | MIT | Sehr hoch | Webframework-Kern; Modellaufrufe in eigener Anwendung ergänzen. | PostgreSQL: [EF Core mit Npgsql](https://www.npgsql.org/efcore/) |
| 2 | [Django](https://github.com/django/django) | BSD-3-Clause | Sehr hoch | Webframework-Kern mit ORM; Modell- und Vektoranbindung zusätzlich entwickeln. | PostgreSQL: [Offizielles PostgreSQL-Backend](https://docs.djangoproject.com/en/stable/ref/databases/#postgresql-notes) |
| 3 | [FastAPI](https://github.com/fastapi/fastapi) | MIT | Sehr hoch | Asynchrones Python-API-Framework für latenzarmes Token-Streaming und Modell-Gateways. | PostgreSQL: [Eigene SQLAlchemy-Anbindung über PostgreSQL-Dialekt](https://docs.sqlalchemy.org/en/20/dialects/postgresql.html) |
| 4 | [Symfony](https://github.com/symfony/symfony) | MIT | Sehr hoch | PHP-Webframework; Modellaufrufe in eigenen Diensten ergänzen. | PostgreSQL: [Doctrine und PostgreSQL-Anbindung](https://symfony.com/doc/current/doctrine.html) |
| 5 | [Spring Boot](https://github.com/spring-projects/spring-boot) / [Spring AI](https://github.com/spring-projects/spring-ai) | Apache-2.0 | Hoch | Dokumentierte Java-Abstraktion für Chat-Clients, Prompt-Templates und pgvector-Stores. | PostgreSQL: [pgvector-Integration via Spring AI](https://docs.spring.io/spring-ai/reference/api/vectordbs/pgvector.html) |

## Einsatz und Abgrenzung

Die Tabelle unterscheidet den Webframework-Kern von einer selbst entwickelten
Modellanbindung. Bei Spring AI ist eine konkrete KI-Bibliothek benannt; bei den
übrigen Frameworks müssen Modellaufruf, Fehlerbehandlung und Berechtigungen in
der Anwendung ergänzt werden.

PostgreSQL wird serverseitig über das genannte ORM oder einen Treiber angebunden.
Vektorsuche und Konversationsspeicherung sind getrennte Integrationsaufgaben.
Eine PostgreSQL-Verbindung allein liefert noch keinen Agenten.

Streaming kann in einer geeigneten HTTP-Antwort umgesetzt werden. Eine
Warteschlange ist für längere Hintergrundaufgaben hilfreich, aber keine
allgemeine Voraussetzung für jede gestreamte Antwort. Laufzeitgrenzen und
Verbindungsabbrüche müssen behandelt werden.
