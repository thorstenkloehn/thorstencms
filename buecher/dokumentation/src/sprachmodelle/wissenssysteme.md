# Sprachmodelle in Wissenssystemen

[Übergeordnete Kategorie: Integration von Sprachmodellen in Software-Architekturen](../sprachmodell-integration.md)

Semantische Wissensgraphen, Local-First PKM mit Sprachmodellen und RAG-gestützte Recherche mit Quellennachweisen.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [SiYuan](https://github.com/siyuan-note/siyuan) | AGPL-3.0 | Sehr hoch | Block-basierter Wissensgraph mit lokaler semantischer Suche und integriertem KI-Assistenten. | Dateien: [Lokales JSON-Dateisystem im Workspace](https://github.com/siyuan-note/siyuan/blob/master/docs/WORKSPACE.md) |
| 2 | [Dify](https://github.com/langgenius/dify) | Apache-2.0 | Hoch | Etablierte Plattform für visuelle RAG-Workflows, Agenten und strukturierte Wissensbasen. | PostgreSQL: [PostgreSQL als zentrale Anwendungs- und Vektordatenbank](https://docs.dify.ai/) |
| 3 | [RAGFlow](https://github.com/infiniflow/ragflow) | Apache-2.0 | Hoch | Tiefgehende Dokumentenextraktion (PDF, Tabellen, OCR) mit belegbarem RAG-Abruf. | PostgreSQL: [PostgreSQL für relationale Metadaten](https://ragflow.io/) |
| 4 | [Wiki.js](https://js.wiki/about) | AGPL-3.0 | Hoch | Modernes Wissensportal mit konfigurierbarer Volltext- und Vektor-Suchintegration. | PostgreSQL: [Unterstütztes Datenbank-Backend](https://js.wiki/get-started) |
| 5 | [AnythingLLM](https://github.com/Mintplex-Labs/anything-llm) | MIT | Mittel | Dokumentenbasiertes Arbeitsplatzsystem mit flexibler Vektorspeicheranbindung. | PostgreSQL: [PostgreSQL-Schema und pgvector-Setup](https://github.com/Mintplex-Labs/anything-llm) |

## Einsatz und Abgrenzung

Wissenssysteme nutzen Sprachmodelle zur Verknüpfung unstrukturierter Inhalte und zur Verhinderung von Halluzinationen.

- **SiYuan:** Perfekt für individuelle Wissensgraphen; RAG-Abfragen erfolgen primär auf dem lokalen, dateibasierten Datenbestand.
- **Dify:** Hoher Bedienkomfort durch visuelle Orchestrierung; Docker-/Kubernetes-Betrieb für Teams empfohlen.
- **RAGFlow:** Exzellente Stärken bei komplexen Layouts und Tabellen; höherer Rechenaufwand bei der Dokumentenextraktion.
- **Wiki.js:** Strukturiertes Unternehmens-Wiki; RAG-Funktionalität setzt externe KI-Endpunkte voraus.
- **AnythingLLM:** Schneller Einstieg für Desktop- und Serverumgebungen; erfordert explizite pgvector-Konfiguration.
