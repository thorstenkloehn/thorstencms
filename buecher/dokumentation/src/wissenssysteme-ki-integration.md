# Wissenssysteme und KI-Framework-SDKs

Ein digitales Wissenssystem – sei es ein Dokumentationsportal, ein internes Wiki oder ein organisationsweiter Wissensgraph – dient der strukturierten Ablage, Vernetzung und Auffindbarkeit von Informationen. Die Integration moderner KI-Framework-SDKs erweitert solche Systeme von der reinen Volltextrecherche hin zu semantischer Suche, automatisierter Synthese und interaktiver Beantwortung komplexer Fragestellungen (Retrieval-Augmented Generation, RAG).

Im Gegensatz zu einfachen Chatbots oder generischen Webanwendungen stellt ein Wissenssystem besondere Anforderungen an die technische Modellintegration:

* **Strikte Belegbarkeit:** Aussagen eines Modells sind im Wissensmanagement wertlos, wenn sie nicht präzise durch Fundstellen (Dokumente, Kapitel, Versionsstände) nachgewiesen werden können.
* **Inhaltliche Dynamik und Konsistenz:** Wissensbestände verändern sich kontinuierlich. Vektorindizes und Metadaten müssen inkrementell aktualisiert werden, ohne dass veraltete Passagen als Fakten weitergegeben werden.
* **Granulare Zugriffssteuerung (ACLs):** Ein Benutzer darf über den KI-Assistenten ausschließlich Antworten erhalten, die auf Dokumenten basieren, für die er eine Leseberechtigung besitzt.

```
┌─────────────────────────────────────────────────────────────┐
│                 Wissenssystem / Redaktion                   │
│         (Markdown-Dateien, Wikis, PDFs, Relationen)         │
└──────────────────────────────┬──────────────────────────────┘
                               │ Ingestion-Pipeline
┌──────────────────────────────▼──────────────────────────────┐
│ Vorverarbeitung & Indizierung                                │
│  ├─ Strukturbewusstes Chunking (Überschriften, Absätze)     │
│  ├─ Metadaten-Extraktion (Autor, Berechtigung, Datum)       │
│  └─ Embedding-Generierung über Modell-SDKs                  │
└──────────────────────────────┬──────────────────────────────┘
                               │ Vektoren & Chunks
┌──────────────────────────────▼──────────────────────────────┐
│ Hybride Datenhaltung: PostgreSQL / pgvector                  │
│  ├─ Lexikalische Volltextindizes (tsvector / BM25)          │
│  ├─ Vektorindizes (HNSW / IVFFlat mit Kosinus-Distanz)      │
│  └─ Relationale Metadaten & Zugriffskontrolllisten (ACL)    │
└──────────────────────────────▲──────────────────────────────┘
                               │ Gefilterter semantischer Abruf
┌──────────────────────────────▼──────────────────────────────┐
│ Retrieval- & Orchestrierungs-Schicht (KI-Framework-SDK)     │
│  ├─ Hybrides Retrieval & Re-Ranking (Cross-Encoder)         │
│  ├─ Prompt-Zusammenstellung mit striktem Grounding          │
│  └─ Zitier- und Quellenverweis-Generierung                  │
└──────────────────────────────▲──────────────────────────────┘
                               │ Belegte Antwort mit Links
┌──────────────────────────────┴──────────────────────────────┐
│                    Leser / Wissensarbeiter                  │
└─────────────────────────────────────────────────────────────┘
```

---

## Kernprinzipien der Integration

1. **Kein Modell ohne Kontext (Grounding):** Das Sprachmodell agiert nicht als Wissensspeicher, sondern ausschließlich als sprachlicher Synthese- und Formulierungsprozessor für die übergebenen Dokumentenfragmente.
2. **Hybride Suche statt reiner Vektoren:** Vektorsuche allein scheitert oft an exakten Bezeichnern, Artikelnummern oder seltenen Fachbegriffen. Eine Kombination aus lexikalischer Volltextsuche und Vektorsuche liefert die stabilsten Treffer.
3. **Filterung vor der Inferenz (Pre-Filtering):** Berechtigungen dürfen nicht erst nach der Antwortgenerierung geprüft werden. Die Suche im Vektorspeicher muss zwingend auf die Dokumenten-IDs eingeschränkt werden, für die der anfragende Benutzer leseberechtigt ist.

---

## Unterkategorien dieses Kapitels

Die technischen Herausforderungen und Entwurfsmuster gliedern sich in drei Schwerpunkte:

* [Dokumentenaufnahme, Chunking und Synchronisation](wissenssysteme-ki-integration/ingestion-chunking.md): Struktur- und Markdown-bewusstes Zerlegen von Texten, Einbettungsgenerierung und inkrementelle Index-Aktualisierung.
* [Hybride Suche, Re-Ranking und Quellenbelege](wissenssysteme-ki-integration/hybrid-retrieval-reranking.md): Verknüpfung von BM25 und Vektorsuche, Re-Ranking zur Vermeidung des „Lost in the Middle“-Effekts und präzise Zitierlogik.
* [Zugriffsrechte, Metadatenfilter und Governance](wissenssysteme-ki-integration/rechte-acl-governance.md): Durchsetzung von Benutzerrechten bei der Vektorsuche (ACL-Filterung), Schutz sensibler Daten und Erkennung widersprüchlicher Quellen.

---

> [!NOTE]
> Geprüfte Open-Source-Bibliotheken für Wissenssysteme wie Haystack und LlamaIndex werden im Abschnitt [Sprachmodelle in Wissenssystemen](sprachmodelle/wissenssysteme.md) bewertet.
