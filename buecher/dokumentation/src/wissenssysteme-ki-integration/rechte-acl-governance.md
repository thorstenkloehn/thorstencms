# Zugriffsrechte, Metadatenfilter und Governance

[Übergeordnete Kategorie: Wissenssysteme und KI-Framework-SDKs](../wissenssysteme-ki-integration.md)

In Unternehmen und Organisationen ist Wissen selten für alle Personen gleichermaßen freigegeben. Handbücher, Strategiepapiere, Personalakten und interne Projektberichte unterliegen differenzierten Zugriffskontrolllisten (Access Control Lists / ACLs). Wird ein KI-Framework-SDK ohne strikte Rechteprüfung an ein Wissenssystem angebunden, droht der unbefugte Abruf vertraulicher Daten durch indirekte Prompt-Manipulation oder assoziative Fragen.

---

## Pre-Filtering vs. Post-Filtering bei der Vektorsuche

Die Durchsetzung von Benutzerberechtigungen bei der semantischen Suche kann architektonisch auf zwei Wegen erfolgen:

```
Vorgehen 1: Post-Filtering (Fehleranfällig & Ineffizient)
[Suchanfrage] ──► [Globaler Vektorspeicher] ──► [Top 10 Treffer] ──► [Rechteprüfung] ──► [0 bis 2 Treffer übrig]
                                                                        (Vertrauliche Dokumente
                                                                         werden verworfen)

Vorgehen 2: Pre-Filtering (Empfohlen & Deterministisch)
[Suchanfrage] ──► [SQL WHERE mit Benutzer-Rollen] ──► [HNSW-Vektorsuche] ──► [Top 10 berechtigte Treffer]
                   WHERE acl_groups && :user_roles
```

### Warum Post-Filtering in der Praxis versagt:
Beim Post-Filtering sucht die Vektordatenbank die semantisch ähnlichsten Textblöcke über den gesamten Dokumentenbestand. Erst im Anschluss filtert das Webframework jene Treffer heraus, für die der Benutzer keine Leserechte besitzt.
* **Das Leere-Ergebnis-Problem:** Handelt es sich bei den sechs besten Treffern um vertrauliche Vorstandsprotokolle, werden diese verworfen. Dem Modell verbleiben nur noch vier minderwertige oder gar keine Treffer – die Antwortqualität bricht ein, obwohl im öffentlichen Dokumentenbestand genügend relevante Passagen vorhanden wären.
* **Informationslecks:** Bei fehlerhafter Filterung können vertrauliche Fragmente in den Modellkontext gelangen und dem Benutzer unbeabsichtigt preisgegeben werden.

### Pre-Filtering in PostgreSQL / pgvector:
Beim Pre-Filtering wird die Vektorsuche unmittelbar mit relationalen Metadatenkriterien verknüpft:

```sql
SELECT c.content, c.document_path, (c.embedding <=> :query_embedding) AS distance
FROM knowledge_chunks c
JOIN documents d ON c.document_id = d.id
WHERE d.tenant_id = :current_tenant
  AND d.status = 'published'
  AND d.acl_groups && :user_group_array
ORDER BY distance ASC
LIMIT 10;
```
Der HNSW- oder IVFFlat-Index von `pgvector` durchsucht nur jene Vektoren, die die `WHERE`-Bedingung erfüllen. Der anfragende Benutzer erhält garantiert die zehn besten Treffer, die für seine Sicherheitsstufe freigegeben sind.

---

## Metadatenfilter: Versionen und Gültigkeit

Wissenssysteme enthalten häufig veraltete Versionen, historische Richtlinien oder unfertige Entwürfe. Ein Sprachmodell kann ohne Metadatenfilter nicht erkennen, ob eine gefundene Passage aus dem Jahr 2021 stammt oder der aktuellen Norm entspricht.

### Erforderliche Metadaten an jedem Chunk:
* **Versionsstand (`version`):** Abfragen dürfen standardmäßig nur Chunks der aktiven Version (`version = 'latest'`) adressieren, es sei denn, der Benutzer sucht explizit in einem Versionsarchiv.
* **Veröffentlichungsstatus (`status`):** Entwürfe (`status = 'draft'`) dürfen ausschließlich den jeweiligen Autoren oder Reviewern zugänglich sein.
* **Gültigkeitszeitraum (`valid_until`):** Befristete Dokumente müssen automatisch aus dem aktiven Retrieval-Pool herausfallen, um widersprüchliche Antworten zu verhindern.

---

## Governance und Nachvollziehbarkeit (Audit Trail)

Da die vom Modell generierten Antworten zur Entscheidungsfindung im Unternehmen genutzt werden, müssen alle RAG-Transaktionen nachvollziehbar protokolliert werden:

1. **Kontext-Protokollierung:** Speicherung der Anfrage, der Benutzer-ID, der übergebenen Chunks (inklusive Hash und Dokumentenpfad) und der generierten Antwort in einer relationalen Audit-Tabelle in PostgreSQL.
2. **Datenschutz und PII-Filterung:** Personenbezogene Daten (Personally Identifiable Information wie Telefonnummern, private Adressen, Kreditkartendaten) sollten bereits während der Ingestion-Pipeline maskiert oder anonymisiert werden, bevor sie in Vektorspeicher und externe Modell-APIs gelangen.
3. **Widerspruchserkennung:** Enthält der abgerufene Kontext sich widersprechende Anweisungen aus zwei gleichrangigen Dokumenten, muss die Orchestrierungsschicht dies erkennen und den Benutzer auf den redaktionellen Konflikt hinweisen, anstatt eigenmächtig eine Variante zu bevorzugen.

---

> [!NOTE]
> Die Anbindung von Webanwendungen und Hintergrund-Warteschlangen für derartige Workflows wird im Kapitel [Webframeworks und KI-Framework-SDKs](../web-ki-integration.md) behandelt.
