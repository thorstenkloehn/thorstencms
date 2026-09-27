# Content-Management-Systeme und KI-Framework-SDKs

Content-Management-Systeme (CMS) bilden das redaktionelle Rückgrat für Websites, Portale und digitale Publikationen. Während Wissenssysteme auf die Vernetzung und Auffindbarkeit von Informationen abzielen, liegt der Kern eines CMS in der strukturierten Erstellung, Qualitätssicherung, Versionierung und gezielten Auslieferung von Inhalten an definierte Zielgruppen.

Die Integration von KI-Framework-SDKs in ein CMS unterscheidet sich fundamental von allgemeinen Chat-Schnittstellen:

* **Keine automatische Veröffentlichung (Human-in-the-Loop):** Ein Sprachmodell darf niemals direkt Inhalte in die öffentliche Auslieferung schreiben. Alle generierten Texte, Übersetzungen oder Zusammenfassungen sind Entwürfe (Drafts), die einer redaktionellen Sichtung und Freigabe bedürfen.
* **Feld- und schemabasierte Inhaltsmodelle:** Inhalte in modernen CMS bestehen nicht aus monolithischen Textwüsten, sondern aus typisierten Feldern (Titel, Teaser, Fließtextblöcke, Autorenzuordnung, Taxonomien und SEO-Metadaten). KI-SDKs müssen strukturierte Daten liefern, die exakt in diese Schemata passen.
* **Trennung von Redaktion und Auslieferung:** Redaktionelle KI-Assistenten unterstützen Redakteure im Administrationsbereich (Backend). Die öffentlich ausgelieferten Seiten (Frontend) müssen hingegen statisch oder gecacht sein; Live-Inferenz bei regulären Seitenaufrufen ist wegen Latenz und Kosten strikt zu vermeiden.

```
┌─────────────────────────────────────────────────────────────┐
│                    Redaktionsumgebung (UI)                  │
│       (Block-Editor, Formularfelder, Medienbibliothek)      │
└──────────────────────────────▲──────────────────────────────┘
                               │ HTTP / SSE / REST
┌──────────────────────────────▼──────────────────────────────┐
│ CMS-Kern / Backend-Logik (Drupal, Headless CMS, etc.)       │
│  ├─ Rollen & Workflow-Status (Draft, Review, Published)     │
│  ├─ Validierung gegen Content-Type-Schema (Pydantic / JSON) │
│  └─ Revisionshistorie & Diff-Tracking                       │
└──────────────────────────────▲──────────────────────────────┘
                               │ Asynchroner Event-Bus / Webhook
┌──────────────────────────────▼──────────────────────────────┐
│ KI-Integrations-Schicht (Framework-SDK)                     │
│  ├─ Strukturierte Textgenerierung (Structured Outputs)      │
│  ├─ Taxonomie-Klassifizierung & Verschlagwortung            │
│  └─ Multimodale Bildanalyse (Alt-Texte, Barrierefreiheit)   │
└──────────────────────────────▲──────────────────────────────┘
                               │ SQL / Relationen
┌──────────────────────────────▼──────────────────────────────┐
│ Persistenzschicht: PostgreSQL (Inhalte, Entwürfe, Revisionen│
└─────────────────────────────────────────────────────────────┘
```

---

## Kernaufgaben der CMS-Integration

1. **Staging und Revisionssicherheit:** Jeder KI-generierte Textvorschlag muss in der Revisionshistorie des CMS als maschineller Entwurf gekennzeichnet werden. Autoren müssen per visueller Diff-Ansicht prüfen können, welche Passagen unverändert übernommen oder redigiert wurden.
2. **Taxonomie- und Metadaten-Generierung:** Das Extrahieren konsistenter Schlagwörter (Tags), Kategorien und SEO-Metadaten entlastet Redakteure, muss sich aber an bestehenden kontrollierten Vokabularen des CMS orientieren.
3. **Event-getriebene Headless-Pipelines:** In entkoppelten (Headless) CMS-Architekturen läuft die KI-Veredelung (wie Übersetzung oder Zusammenfassung) bevorzugt im Hintergrund über Webhooks ab, um den Redaktionsfluss nicht zu blockieren.

---

## Unterkategorien dieses Kapitels

Die technischen Integrationsmuster gliedern sich in drei Schwerpunkte:

* [Redaktionelle Workflows und Freigabeprozesse](cms-ki-integration/redaktionelle-workflows-freigabe.md): Staging von KI-Entwürfen, Diff-Prüfung, Revisionshistorie und die Vermeidung automatisierter Veröffentlichungen.
* [Strukturierte Inhaltserstellung und Metadaten-Extraktion](cms-ki-integration/strukturierte-inhalte-metadaten.md): Schema-konforme Feldgenerierung (Structured Outputs), Taxonomie-Klassifizierung und barrierefreie Alt-Texte.
* [Headless-Architekturen, Webhooks und Event-Pipelines](cms-ki-integration/headless-webhooks-automation.md): Asynchrone Content-Veredelung über CMS-Webhooks, Entkopplung von Inferenzzeiten und Edge-Caching.

---

> [!NOTE]
> Die qualitative Bewertung von CMS-Erweiterungen am Beispiel von Drupal AI findet sich im Kapitel [Sprachmodelle in Content-Management-Systemen](sprachmodelle/cms.md). Konzeptionelle Grundlagen zu Headless- und Composable-Architekturen sind unter [Content-Management-Systeme](cms.md) dokumentiert.
