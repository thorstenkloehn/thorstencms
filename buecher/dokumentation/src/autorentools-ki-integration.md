# Autorentools und KI-Framework-SDKs

Autorentools, Textprozessoren und Office-Suites (wie OnlyOffice, LibreOffice oder Markdown-Editoren) sind die primäre Arbeitsumgebung für Verfasser von Büchern, wissenschaftlichen Artikeln, Verträgen und technischen Dokumentationen. Im Unterschied zu CMS-Plattformen oder Git-basierten Repositories steht hier nicht der Publikations- oder Build-Workflow im Vordergrund, sondern der unmittelbare **Schreib-, Redigier- und Denkprozess am Text**.

Die Einbindung von KI-Framework-SDKs in Autorentools verändert die Interaktion zwischen Mensch und Text:

* **Kontextbezogene Echtzeit-Interaktion:** Die KI agiert direkt an der aktuellen Cursor-Position. Sie unterstützt Autoren über Vervollständigungsvorschläge (Ghost-Text) oder die gezielte Überarbeitung markierter Passagen.
* **Format- und Strukturerhalt:** Autoren arbeiten selten mit reinem ASCII-Text. Fußnoten, Querverweise, Überschriftenhierarchien und typografische Auszeichnungen (DOCX, ODT oder Markdown) müssen bei maschinellen Überarbeitungen zwingend intakt bleiben.
* **Hohe Schutzbedürftigkeit unveröffentlichter Werke:** Buchmanuskripte, journalistische Recherchen, Gutachten und Verträge unterliegen strenger Vertraulichkeit. Autorensoftware muss garantieren, dass Texte nicht unbemerkt auf Cloud-Servern Dritter gespeichert oder für Modelltrainings verwendet werden.

```
┌─────────────────────────────────────────────────────────────┐
│                    Autorenumgebung / UI                     │
│        (Rich-Text-Editor, Cursor, Dokumentenstruktur)       │
└──────────────────────────────▲──────────────────────────────┘
                               │ Plugin-API / Event-Handler
┌──────────────────────────────▼──────────────────────────────┐
│ Editor-Erweiterung (In-App-Integration)                     │
│  ├─ Kontext-Extraktion (Prefix vor Cursor, Suffix danach)   │
│  ├─ Formatierungs-Sanitizing (DOM / AST-Schutz)             │
│  └─ Asynchroner Render-Thread (Non-blocking UI-Streaming)   │
└──────────────────────────────▲──────────────────────────────┘
                               │ Typsichere Methodenaufrufe
┌──────────────────────────────▼──────────────────────────────┐
│ KI-Integrations-Schicht (Framework-SDK)                     │
│  ├─ In-line-Vervollständigung & Stilprüfung                 │
│  ├─ Routing: Lokales Modell (Ollama) vs. Cloud-Endpunkt     │
│  └─ Revisions-Tagging (Kennzeichnung maschineller Eingriffe)│
└──────────────────────────────▲──────────────────────────────┘
                               │ Dateisystem / Revisionsspeicher
┌──────────────────────────────▼──────────────────────────────┐
│ Dokumentenspeicherung: Lokale Dateien (DOCX, ODT, Markdown) │
└─────────────────────────────────────────────────────────────┘
```

---

## Kernaufgaben der Autorentool-Integration

1. **Reaktive Benutzeroberfläche ohne Blockaden:** Modellaufrufe dürfen niemals den Haupt-Thread des Editors blockieren. Das Generieren von Text muss asynchron gestreamt werden, sodass der Autor jederzeit weitertippen oder den Vorschlag abbrechen kann.
2. **Integration in die Änderungsverfolgung (Track Changes):** Textänderungen dürfen den bestehenden Inhalt nicht blind überschreiben. Vorschläge müssen sich nahtlos in die native Änderungsverfolgung des Editors einfügen.
3. **Datensouveränität durch lokale Inferenz:** Für sensible Manuskripte muss die Architektur den Betrieb lokaler Open-Weights-Modelle unterstützen, die vollständig offline auf dem Rechner des Autors laufen.

---

## Unterkategorien dieses Kapitels

Die konkreten Implementierungsmuster gliedern sich in drei Schwerpunkte:

* [In-line-Assistenz, Cursor-Kontexte und Ghost-Text](autorentools-ki-integration/inline-assistenz-cursor.md): Asymmetrisches Prompting (Prefix/Suffix), asynchrones Token-Streaming direkt ins Editor-DOM und Erhalt von Dokumentenformatierungen.
* [Änderungsverfolgung, Revisionsmodi und Stilprüfung](autorentools-ki-integration/aenderungsverfolgung-revision.md): Integration in native Office-Revisionsmodi, selektives Akzeptieren von Absätzen und Kopplung an deterministische Styleguides.
* [Vertraulichkeit, Manuskriptschutz und lokale Inferenz](autorentools-ki-integration/datensouveraenitaet-lokale-modelle.md): Schutz unveröffentlichter Texte vor Datenabfluss, Anbindung lokaler Laufzeiten (Ollama / GGUF) und vertragliche Schutzmechanismen.

---

> [!NOTE]
> Die qualitative Einordnung konkreter Desktop-Lösungen wie ONLYOFFICE Desktop Editors findet sich im Kapitel [Sprachmodelle in Office- und Autorentools](sprachmodelle/office-autorentools.md).
