# In-line-Assistenz, Cursor-Kontexte und Ghost-Text

[Übergeordnete Kategorie: Autorentools und KI-Framework-SDKs](../autorentools-ki-integration.md)

Die direkte Unterstützung während des Tippens erfordert eine hochgradig reaktive Schnittstelle zwischen der Text-Engine des Editors und dem KI-Framework-SDK. Anders als bei getrennten Chat-Seitenleisten findet die Interaktion unmittelbar an der Cursor-Position statt.

---

## Das Fill-In-the-Middle-Prinzip (Prefix- und Suffix-Kontext)

Wird ein Textabsatz mitten im Dokument überarbeitet oder fortgeführt, reicht es nicht aus, dem Modell lediglich den vorangegangenen Text zu übergeben. Das Modell muss wissen, wie der Satz oder Absatz nach der Einfügemarke weitergeht, um logische und grammatikalische Brüche zu vermeiden:

```
[Bestehender Text vor Cursor (Prefix)]
"Die Untersuchung ergab signifikante Unterschiede in der Gruppe A, "
                                  ▲
                         [Aktuelle Cursor-Position]
                                  │
                   [KI generiert passenden Einschub]
                   "wobei insbesondere die Latenzwerte ..."
                                  ▼
[Bestehender Text nach Cursor (Suffix)]
"was die ursprüngliche Hypothese der Autoren stützt."
```

### Prompt-Architektur für Text-Vervollständigungen:
* **Prefix (Linker Kontext):** Typischerweise 1.000 bis 3.000 Tokens vor der Cursor-Position zur Erfassung des Gedankengangs und des Schreibstils.
* **Suffix (Rechter Kontext):** 500 bis 1.000 Tokens nach der Cursor-Position, um den grammatikalischen Anschluss an den Folgetext zu sichern.
* **Dokumentenmetadaten:** Titel des Manuskripts, Zielgruppe und Genre werden im System-Prompt verankert.

---

## Ghost-Text und tastaturgesteuerte Interaktion

Die Einblendung maschineller Fortsetzungen erfolgt über sogenannten **Ghost-Text** (halbtransparente, graue Schrift unmittelbar hinter der Einfügemarke):

1. **Nicht-invasives Erscheinen:** Nach einer kurzen Tipp-Pause (Debounce-Intervall von ca. 300 bis 500 Millisekunden) fordert das Editor-Plugin einen kurzen Textchunk über das KI-SDK an.
2. **Schlanke Tastatur-Steuerung:**
   * `Tab`: Übernimmt den gesamten Vorschlag in das Dokument.
   * `Strg + Pfeil rechts`: Übernimmt den Vorschlag schrittweise wortweise.
   * `Escape` oder Weitertippen: Verwirft den Ghost-Text sofort, ohne den Schreibfluss zu unterbrechen.
3. **Geringe Latenz:** Inferenz-Latenzen über 800 Millisekunden zerstören das Schreibgefühl. Für Ghost-Text kommen daher bevorzugt spezialisierte, kompakte Modelle mit hoher Ausgabegeschwindigkeit zum Einsatz.

---

## Erhalt semantischer Formatierungen und DOM-Schutz

Wird eine markierte Textpassage überarbeitet (z. B. *„Absatz kürzen und präziser formulieren“*), besteht die Gefahr, dass Rich-Text-Auszeichnungen zerstört werden.

* **Format-Integrität:** Befinden sich im markierten Bereich Fettungen, Kursivierungen, Fußnotenmarker (`[^1]`) oder Querverweise, muss das KI-SDK angewiesen werden, diese Tags syntaktisch exakt beizubehalten.
* **DOM- und AST-Sanitizing:** Vor dem Zurückschreiben in das Dokument prüft das Plugin die Antwort auf Wohlgeformtheit (z. B. Schließen aller geöffneten XML-/HTML-Knoten oder Markdown-Formatierungszeichen).
* **Asynchrone Entkopplung:** Um ein Einfrieren der Programmoberfläche (UI-Freeze) zu verhindern, laufen Inferenz und Netzwerkabfragen in separaten Hintergrund-Threads (oder Web Workern). Der Haupt-Thread verarbeitet Benutzereingaben jederzeit ohne Verzögerung.

---

> [!NOTE]
> Wie vorgeschlagene Änderungen im Dokument sichtbar gemacht und vom Autor verwaltet werden, zeigt die Unterkategorie [Änderungsverfolgung, Revisionsmodi und Stilprüfung](aenderungsverfolgung-revision.md).
