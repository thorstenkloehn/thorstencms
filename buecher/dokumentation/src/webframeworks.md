# Webframeworks: Darstellung, Verarbeitung und Datenzugriff

Eine Webanwendung nimmt Anfragen entgegen, verarbeitet Eingaben und liefert
eine Antwort. Ein Framework unterstützt diese Aufgaben, legt aber nicht für
jedes Projekt fest, wo Inhalte gespeichert werden oder wie viel Arbeit im
Browser stattfindet.

## Beispiel: Vom Lesekatalog zur Kursanmeldung

Ein selten geänderter Lesekatalog kann als statische Website ausgegeben werden.
Für eine Kursanmeldung kommen Benutzerrechte, Eingabeprüfung und dauerhafte
Speicherung hinzu. Interaktive Bedienung lässt sich schrittweise ergänzen,
ohne die gesamte Anwendung als Single-Page-Application aufzubauen.

Serverseitiges Rendering, Browserkomponenten und statische Ausgabe lassen sich
kombinieren. Islands begrenzen beispielsweise die interaktiven Bereiche einer
Seite; Edge-Betrieb beschreibt den Ausführungsort. Diese Entscheidungen sind
von der Wahl der Datenbank zu unterscheiden.

## Unterkategorien

- [Serverseitige Frameworks](webframeworks/serverseitig.md)
- [Ajax und progressive Erweiterung](webframeworks/ajax.md)
- [Single-Page-Applications](webframeworks/spa.md)
- [Full-Stack- und Meta-Frameworks](webframeworks/meta-frameworks.md)
- [Server Components, Islands und Edge](webframeworks/islands-edge.md)
- [KI-Bausteine und Entwicklungsassistenten](webframeworks/ki-agenten.md)
- [Batteries-Included-Webframeworks](webframeworks/batteries-included.md)
- [Enterprise-Webframeworks](webframeworks/enterprise.md)

Die Kategorien beschreiben Architektur- und Einsatzschwerpunkte. Sie sind
kein verbindliches historisches Generationenmodell.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**. [Bewertungskriterien und Grenzen](software.md).

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

**Einordnung von ASP.NET Core:** Serverseitiges Framework der Enterprise-Linie.
Die Auswahl verwendet PostgreSQL über Npgsql; SQL Server ist dafür nicht erforderlich.
Die Auswahl deckt Python, Ruby, Java, PHP und .NET ab. Weitere passende
Frameworks werden in den Unterkategorien beschrieben.
