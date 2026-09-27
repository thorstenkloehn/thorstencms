# Redaktionelle Workflows und Freigabeprozesse

[Übergeordnete Kategorie: Content-Management-Systeme und KI-Framework-SDKs](../cms-ki-integration.md)

In redaktionellen Umgebungen tragen Herausgeber und Redakteure die juristische und publizistische Verantwortung für veröffentlichte Inhalte. Ein KI-Modell besitzt weder Urteilsfähigkeit noch rechtliche Verantwortlichkeit. Aus diesem Grund verbietet sich eine direkte Veröffentlichung KI-generierter Inhalte ohne menschliche Prüfung von selbst.

---

## Das redaktionelle Staging-Modell

Um Fehlern, Halluzinationen oder unpassender Tonalität vorzubeugen, muss die Integration von KI-Framework-SDKs in die bestehende Workflow-Zustandsmaschine des CMS eingebunden werden:

```
[Redakteur fordert Textentwurf an]
              │
              ▼
┌─────────────────────────────────────────────────────────────┐
│ 1. Status: "AI Draft" (Maschineller Vorschlag)              │
│    ├─ Erzeugt durch KI-Framework-SDK                        │
│    ├─ Als gesonderte Revisionsfassung in PostgreSQL abgelegt│
│    └─ Keine öffentliche Sichtbarkeit im Frontend            │
└──────────────────────────────┬──────────────────────────────┘
                               │ Übergabe an Redaktion
┌──────────────────────────────▼──────────────────────────────┐
│ 2. Status: "In Review" (Redaktionelle Sichtung)             │
│    ├─ Visuelle Diff-Ansicht (Vorschlag vs. Quelltext)       │
│    ├─ Manuelle Korrektur, Faktenprüfung & Stilprüfung       │
│    └─ Prüfung auf Urheberrechtskonformität                  │
└──────────────────────────────┬──────────────────────────────┘
                               │ Explizite Freigabe
┌──────────────────────────────▼──────────────────────────────┐
│ 3. Status: "Published" (Öffentliche Veröffentlichung)       │
│    ├─ Freigegeben durch namentlich benannten Redakteur      │
│    └─ Archivierung der Entwurfsmetadaten im Audit-Log       │
└─────────────────────────────────────────────────────────────┘
```

### Strikte Berechtigungsgrenzen für das KI-SDK:
* **Keine Schreibberechtigung auf `Published`:** Der API-Schlüssel oder das Dienstkonto des KI-SDKs darf auf Datenbankebene ausschließlich Berechtigungen besitzen, neue Revisionen oder Datensätze im Zustand `AI Draft` anzulegen.
* **Keine Löschrechte:** Das KI-System darf bestehende Dokumente oder frühere Revisionen weder modifizieren noch löschen.

---

## Diff-Prüfung und Revisionshistorie

Ein Redakteur muss auf einen Blick erkennen können, was die KI vorgeschlagen hat und welche Passagen bereits manuell bearbeitet wurden.

1. **Visuelle Diff-Ansicht:** Im Redaktionsinterface werden Änderungen farblich visualisiert (z. B. grün für Ergänzungen, rot durchgestrichen für Streichungen). Dies erlaubt ein schnelles, zeilenweises Akzeptieren oder Verwerfen von Textvorschlägen.
2. **Revisionsmetadaten:** Zu jeder durch KI erzeugten Revision speichert das CMS unveränderliche Metadaten in PostgreSQL:
   * Verwendetes Modell (z. B. Modellname und Versionsstand)
   * Eingesetzter System-Prompt und Quellkontext
   * Zeitstempel und auslösender Benutzer
3. **Ein-Klick-Rollback:** Sollte ein überarbeiteter Artikel Mängel aufweisen, muss das CMS jederzeit die Wiederherstellung der letzten rein manuell verfassten Fassung ermöglichen.

---

## Urheberrechts- und Qualitätsprüfungen vor der Freigabe

Vor dem Übergang von `In Review` zu `Published` muss der redaktionelle Workflow definierte Prüfschritte erzwingen:
* **Fakten- und Belegprüfung:** Werden statistische Angaben, Zitate oder Produktbezeichnungen im Text genannt, müssen diese gegen die Primärquellen abgeglichen werden.
* **Urheberrechtsprüfung:** Maschinell paraphrasierte Passagen müssen auf Plagiate und unerlaubte Übernahmen aus fremden Quellen überprüft werden.
* **Tonalitätsprüfung:** Passt der Sprachstil (Du/Sie, Fachterminologie, Markenidentität) zu den redaktionellen Richtlinien der Publikation?

---

> [!NOTE]
> Wie KI-SDKs genutzt werden, um nicht nur Fließtext, sondern passgenaue Daten für strukturierte CMS-Felder zu erzeugen, erläutert die Unterkategorie [Strukturierte Inhaltserstellung und Metadaten-Extraktion](strukturierte-inhalte-metadaten.md).
