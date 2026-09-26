# Bücher

## Kategorie: Dokumentation

[Digitale Dokumentation und Wissenssysteme](buecher/dokumentation/src/README.md)
ist ein deutschsprachiges mdBook über Dokumentationsformen und die Entwicklung
von Wissenssystemen, Content-Management-Systemen, Docs-as-Code, Webframeworks, Lernmanagement-Systemen (LMS), Mobile- und Desktop-Apps sowie Sprachmodell-Integrationen.

Status: Thematische Einführungen und gefilterte Open-Source-Auswahlen
für acht Hauptkategorien und 52 Unterkategorien. Enthalten bleiben nur
PostgreSQL- oder dateibasierte Betriebsvarianten, mit Lizenzen, Reifegraden,
Speicherwegen und Quellen. Die Listen enthalten je nach Beleglage bis zu fünf Einträge.
Installationsanleitungen werden später ergänzt.

### Buch bauen und lesen

Voraussetzung: installiertes `mdbook`.

```sh
mdbook build buecher/dokumentation
mdbook serve buecher/dokumentation --open
```

Die erzeugte Website liegt unter `buecher/dokumentation/book/`.
Kapitel und Navigation werden in `buecher/dokumentation/src/` gepflegt.
