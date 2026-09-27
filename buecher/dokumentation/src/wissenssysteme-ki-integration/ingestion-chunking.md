# Dokumentenaufnahme, Chunking und Synchronisation

[Übergeordnete Kategorie: Wissenssysteme und KI-Framework-SDKs](../wissenssysteme-ki-integration.md)

Die Qualität jeder semantischen Antwort in einem Wissenssystem hängt maßgeblich von der Güte der zugrunde liegenden Datenaufnahme (Ingestion) ab. Ein Sprachmodell kann nur so präzise antworten, wie die bereitgestellten Textpassagen strukturiert und semantisch abgegrenzt sind.

---

## Grenzen naiver Textzerlegung

In frühen Implementierungen wurden Dokumente häufig starr nach festen Zeichen- oder Tokengrenzen zerlegt (z. B. alle 500 Zeichen mit 50 Zeichen Überlappung). In professionellen Dokumentations- und Wissenssystemen führt dieses Vorgehen zu schwerwiegenden Problemen:

* **Zerschnittener Kontext:** Sätze, Codebeispiele, Tabellen oder Definitionslisten werden mitten im Inhalt getrennt. Dem Modell fehlt entweder die Bedingung oder die Konsequenz einer Aussage.
* **Verlust hierarchischer Metadaten:** Ein isolierter Absatz über „Berechtigungen“ verliert seine Bedeutung, wenn die übergeordnete Überschrift „Administratoren im Archiv-Modul“ abgeschnitten wird.
* **Redundante Rauscherzeugung:** Kurze Codezeilen oder Kopfzeilen ohne Kontext erzeugen Vektoreinbettungen mit geringem Informationsgehalt, verzerren aber die Ähnlichkeitssuche.

---

## Strukturbewusstes Chunking (Hierarchical Chunking)

Wissenssysteme setzen auf parser-gestütztes, strukturbewusstes Chunking, das den Dokumentenbaum (Abstract Syntax Tree / AST) respektiert:

```
[Markdown- / Wiki-Dokument]
       │
       ▼ AST-Parsing (Überschriften H1, H2, H3, Absätze, Code)
┌─────────────────────────────────────────────────────────────┐
│ Chunk 1: H1 "Rechteverwaltung" > H2 "Rollen"                │
│ Text: "Die Rolle 'Editor' umfasst Schreibrechte für ..."     │
│ Metadaten: { "doc_id": "auth.md", "level": 2, "pos": 14 }   │
├─────────────────────────────────────────────────────────────┤
│ Chunk 2: H1 "Rechteverwaltung" > H2 "Audit-Log" (Tabelle)   │
│ Text: Vollständige Markdown-Tabelle als unteilbarer Block   │
│ Metadaten: { "doc_id": "auth.md", "level": 2, "pos": 38 }   │
└─────────────────────────────────────────────────────────────┘
```

### Best Practices für Wissens-Chunks:
1. **Hierarchische Pfade voranstellen:** Jeder Text-Chunk erhält die Brotkrümelnavigation (Breadcrumbs) der übergeordneten Abschnitte als Textprefix (z. B. `Pfad: Dokumentation > Webframeworks > Caching`). Dadurch bleibt der Kontext auch dann erhalten, wenn der Vektorspeicher nur den isolierten Chunk liefert.
2. **Atomare Einheiten wahren:** Tabellen, JSON-Schemata und Code-Blöcke dürfen nicht zerschnitten werden. Sie müssen entweder als ganzer Block indiziert oder mit einer zusammenfassenden Beschreibung versehen werden.
3. **Optimale Chunk-Größe:** Typische Größen liegen bei 250 bis 800 Tokens. Kleinere Chunks liefern präzisere Vektortreffer, erfordern aber beim Prompting das Zusammenfügen benachbarter Blöcke (Chunk Expansion / Parent-Document Retrieval).

---

## Vektorisierung und Einbettungsmodelle

Das KI-Framework-SDK übergibt die aufbereiteten Textabschnitte an ein Embedding-Modell, das den Text in einen hochdimensionalen Vektor übersetzt (meist zwischen 768 und 3072 Dimensionen).

* **Lokal vs. Cloud-API:** Lokale Modelle (z. B. über Ollama oder HuggingFace Embeddings) garantieren vollständige Datensouveränität, da keine internen Wissensdokumente an Drittanbieter gesendet werden. Cloud-Dienste bieten oft höhere semantische Trennschärfe bei mehrsprachigen Dokumenten, erfordern aber strenge Datenschutzprüfungen.
* **Konsistenz der Vektorräume:** Alle Chunks und alle späteren Suchanfragen müssen zwingend mit **demselben Embedding-Modell** in derselben Version berechnet werden. Ein Modellwechsel erfordert die vollständige Neuberechnung des gesamten Vektorbestands.

---

## Inkrementelle Synchronisation und Cache-Invalidierung

Wissensbestände sind nicht statisch; Artikel werden editiert, verschoben oder gelöscht. Ein periodischer Neuaufbau des gesamten Vektorbestands ist ab wenigen tausend Seiten weder wirtschaftlich noch zeitnah möglich.

### Die inkrementelle Synchronisations-Pipeline:
1. **Hash-basierte Änderungsprüfung:** Für jedes Dokument wird bei der Ingestion ein Prüfsummen-Hash (z. B. SHA-256) über den Quelltext berechnet und in PostgreSQL gespeichert.
2. **Selektive Aktualisierung:** Bei einem Commit oder Dokumenten-Save vergleicht das System den neuen Hash mit dem gespeicherten Wert. Nur geänderte Dateien werden neu geparst und vektorisiert.
3. **Tombstone-Löschung:** Wird ein Dokument oder ein Abschnitt gelöscht, müssen alle zugeordneten Chunks unverzüglich über ihre `doc_id` aus `pgvector` entfernt werden. Andernfalls liefert das System weiterhin veraltete oder gelöschte Inhalte als Antworten (Geister-Zitate).

---

> [!NOTE]
> Wie die so erzeugten Vektoren mit klassischer Volltextsuche verknüpft werden, zeigt die nächste Unterkategorie [Hybride Suche, Re-Ranking und Quellenbelege](hybrid-retrieval-reranking.md).
