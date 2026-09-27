# Hybride Suche, Re-Ranking und Quellenbelege

[Übergeordnete Kategorie: Wissenssysteme und KI-Framework-SDKs](../wissenssysteme-ki-integration.md)

In einem professionellen Wissenssystem entscheidet die Qualität des Informationsabrufs (Retrieval) darüber, ob ein Sprachmodell verlässliche Fakten liefert oder plausible Halluzinationen erzeugt. Eine naive semantische Vektorsuche reicht für technische und fachliche Dokumentationsbestände in der Praxis selten aus.

---

## Die Notwendigkeit hybrider Suche

Moderne Wissensabfragen erfordern die gleichzeitige Bewältigung zweier unterschiedlicher Suchmuster:

1. **Semantische Ähnlichkeit (Dense Retrieval):**
   * Erkennt thematische Zusammenhänge, selbst wenn unterschiedliche Begriffe verwendet werden (z. B. Suchbegriff: *„Benutzerzugänge sperren“*, Dokumentinhalt: *„Deaktivierung von Benutzerkonten im Identitätsmanagement“*).
   * Verwendet Vektoreinbettungen und Distanzmetriken (wie Kosinus-Ähnlichkeit) in `pgvector`.
2. **Lexikalische Exaktheit (Sparse Retrieval / BM25):**
   * Unerlässlich für spezifische Fachbegriffe, Funktionsnamen (`verify_jwt_token()`), Fehlercodes (`ERR_CONNECTION_REFUSED`), Lizenzbezeichnungen oder Akronym-Kombinationen.
   * Verwendet PostgreSQL-Volltextindizes (`tsvector` und `tsquery`).

```
                   ┌─────────────────────────────┐
                   │    Benutzer-Suchanfrage     │
                   └──────────────┬──────────────┘
                                  │
         ┌────────────────────────┴────────────────────────┐
         │                                                 │
         ▼                                                 ▼
┌─────────────────────────────┐                   ┌─────────────────────────────┐
│ Lexikalische Suche (BM25)   │                   │ Vektorsuche (pgvector)      │
│ Findet exakte Bezeichner,   │                   │ Findet semantisch verwandte │
│ Fehlercodes & Funktionsnamen│                   │ Konzepte & Paraphrasen      │
└──────────────┬──────────────┘                   └──────────────┬──────────────┘
               │ Top-50 Ergebnisse                               │ Top-50 Ergebnisse
               └────────────────────────┬────────────────────────┘
                                        ▼
                   ┌─────────────────────────────────────────────┐
                   │ Reciprocal Rank Fusion (RRF)                │
                   │ Zusammenführung & Score-Normalisierung      │
                   └────────────────────┬────────────────────────┘
                                        ▼ Top-20 Kandidaten
                   ┌─────────────────────────────────────────────┐
                   │ Re-Ranking (Cross-Encoder)                  │
                   │ Tiefe Relevanzbewertung von Query + Passage │
                   └────────────────────┬────────────────────────┘
                                        ▼ Beste 3 bis 5 Chunks
                   ┌─────────────────────────────────────────────┐
                   │ Sprachmodell-Prompt mit Quellennachweisen   │
                   └─────────────────────────────────────────────┘
```

---

## Reciprocal Rank Fusion (RRF) und Re-Ranking

### 1. Zusammenführung über RRF
Da die Scores von Vektordistanzen (z. B. 0.82 Kosinus) und Volltext-Rankings (z. B. 0.45 BM25-Score) nicht direkt mathematisch vergleichbar sind, nutzt man Reciprocal Rank Fusion (RRF). RRF bewertet Treffer anhand ihrer relativen Position in beiden Ergebnislisten:

$$RRF(d) = \sum_{m \in M} \frac{1}{k + r_m(d)}$$

Hierbei ist $r_m(d)$ der Rang des Dokuments $d$ im Suchverfahren $m$ und $k$ eine Glättungskonstante (häufig $k = 60$). Dokumente, die in beiden Verfahren vordere Plätze belegen, steigen verlässlich an die Spitze auf.

### 2. Re-Ranking (Cross-Encoder)
Die Top-Kandidaten (z. B. 20 Chunks) werden an ein Re-Ranking-Modell übergeben.
* **Unterschied zum Embedding:** Während Embedding-Modelle Query und Dokument getrennt voneinander in Vektoren übersetzen (Bi-Encoder), analysiert ein Cross-Encoder Suchanfrage und Passage **gemeinsam in einem Durchlauf**. Er erkennt komplexe Verneinungen, temporale Einschränkungen und feine semantische Nuancen.
* **Vermeidung des „Lost in the Middle“-Effekts:** Sprachmodelle neigen dazu, Fakten am Anfang und am Ende eines Prompts besser zu beachten als Passagen in der Mitte. Durch das Re-Ranking wird der Kontext auf die drei bis fünf relevantesten Chunks verdichtet, was sowohl die Antwortpräzision erhöht als auch die Inferenzkosten senkt.

---

## Strikte Zitationslogik und Belegprüfung (Grounding)

Ein Wissenssystem muss transparent machen, worauf eine Aussage beruht.

### Regeln für den System-Prompt:
1. **Keine Spekulation:** Das Modell wird angewiesen, ausschließlich Informationen aus den bereitgestellten Textstücken zu verwenden. Enthält der Kontext keine Antwort, muss das Modell dies explizit formulieren (*„Auf Basis der vorliegenden Dokumentation kann diese Frage nicht beantwortet werden.“*).
2. **Eindeutige Zitationsmarker:** Jeder bereitgestellte Chunk erhält eine eindeutige Kennung (z. B. `[Quelle 1: path/to/doc.md#L45]`). Das Modell muss jede Einzelaussage mit dem entsprechenden Marker belegen.
3. **Interaktive Darstellung im Frontend:** Das Webframework übersetzt die Marker in klickbare Links, die den Benutzer direkt zur zitierten Stelle im Quellartikel führen und die entsprechende Textpassage im Lesemodus hervorheben.

---

> [!NOTE]
> Welche Sicherheits- und Datenschutzvorgaben bei der Abfrage von Wissensquellen gelten, erläutert die Unterkategorie [Zugriffsrechte, Metadatenfilter und Governance](rechte-acl-governance.md).
