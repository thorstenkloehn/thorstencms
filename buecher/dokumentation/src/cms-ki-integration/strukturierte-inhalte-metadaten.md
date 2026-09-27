# Strukturierte Inhaltserstellung und Metadaten-Extraktion

[Übergeordnete Kategorie: Content-Management-Systeme und KI-Framework-SDKs](../cms-ki-integration.md)

Moderne Content-Management-Systeme speichern Inhalte nicht als unstrukturierte HTML- oder Textblöcke, sondern in typisierten Content-Modellen. Ein Artikel setzt sich aus spezifischen Feldern zusammen: Schlagzeile, Untertitel, URL-Slug, Zusammenfassung, Fließtext-Abschnitte, Kategorien, SEO-Metadaten und barrierefreie Bildbeschreibungen. KI-Framework-SDKs müssen in der Lage sein, genau diese Feldstrukturen zuverlässig zu befüllen.

---

## Strukturierte Ausgaben über Typschemata (Structured Outputs)

Die unzuverlässige Extraktion von Daten über Freitext-Prompts („Antworte im JSON-Format“) führte früher oft zu Syntaxfehlern durch vorangestellten Erklärungstext oder unvollständige Klammern. Moderne KI-SDKs erzwingen über **Structured Outputs** die strikte Einhaltung von JSON-Schemata auf Token-Ebene:

```python
from pydantic import BaseModel, Field
from typing import List

class CMSArticleDraft(BaseModel):
    title: str = Field(description="Prägnante Überschrift, max. 65 Zeichen", max_length=65)
    slug: str = Field(description="URL-konformer Kebab-Case-Slug", pattern=r"^[a-z0-9-]+$")
    teaser: str = Field(description="Zusammenfassung für Artikelübersichten, max. 160 Zeichen", max_length=160)
    body_markdown: str = Field(description="Haupttext gegliedert in Markdown-Absätze")
    assigned_tag_ids: List[int] = Field(description="IDs der zutreffenden Tags aus dem kontrollierten Vokabular")
    meta_description: str = Field(description="SEO-Meta-Description, 140 bis 155 Zeichen")
```

Das KI-SDK garantiert, dass die Rückgabe des Modells exakt dieser Struktur entspricht. Das CMS kann die Antwort direkt ohne fehleranfälliges Regex-Parsing in seine Datenbankfelder schreiben.

---

## Taxonomien und kontrollierte Vokabulare

Lässt man ein Sprachmodell Schlagworte frei erzeugen, entstehen innerhalb kürzester Zeit redundante oder inkonsistente Tag-Sammlungen (z. B. nebeneinander existierende Varianten wie *„KI“*, *„Künstliche Intelligenz“*, *„Artificial Intelligence“* und *„künstliche-intelligenz“*).

### Best Practices für kontrollierte Verschlagwortung:
1. **Übergabe des Tag-Katalogs im Prompt:** Das CMS liest alle aktiven Kategorien und Tags aus PostgreSQL aus und übergibt deren Bezeichnungen und IDs als Auswahlmenge an das KI-SDK.
2. **Enum-Beschränkung:** Im JSON-Schema werden die zulässigen Werte auf die vorhandenen IDs beschränkt. Das Modell darf ausschließlich aus dieser Schnittmenge wählen.
3. **Vorschlags-Workflow für neue Tags:** Erkennt das Modell einen neuen thematischen Schwerpunkt, der im Katalog fehlt, darf es diesen nicht eigenmächtig anlegen, sondern muss ihn in einem separaten Feld `suggested_new_tags` eintragen, damit Redakteure ihn prüfen und freigeben können.

---

## Barrierefreie Bildbeschreibungen (Alt-Texte)

Ein wesentlicher Einsatzbereich multimodaler KI-SDKs im CMS ist die Unterstützung der digitalen Barrierefreiheit (a11y) in der Medienbibliothek:

* **Sinnstiftende Alt-Texte:** Multimodale Vision-Modelle analysieren hochgeladene Bilder und generieren präzise Beschreibungen des Dargestellten für Screenreader.
* **Vermeidung von Füllfloskeln:** Durch gezielte System-Prompts wird sichergestellt, dass Floskeln wie *„Ein Bild von...“* oder *„Ein Foto zeigt...“* unterbleiben und stattdessen der funktionale Bildinhalt und erkennbarer Text (OCR) im Fokus stehen.
* **Redaktionelle Bestätigung:** Der generierte Alt-Text wird als Vorschlag in das Bild-Metadatenfeld im CMS eingetragen und kann vom Redakteur vor der Veröffentlichung angepasst werden.

---

> [!NOTE]
> Wie diese Veredelungsschritte in Headless-Architekturen asynchron über Webhooks automatisiert werden, behandelt der Abschnitt [Headless-Architekturen, Webhooks und Event-Pipelines](headless-webhooks-automation.md).
