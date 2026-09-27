# Änderungsverfolgung, Revisionsmodi und Stilprüfung

[Übergeordnete Kategorie: Autorentools und KI-Framework-SDKs](../autorentools-ki-integration.md)

Beim Lektorieren und Überarbeiten literarischer, juristischer oder wissenschaftlicher Texte ist das blinde Überschreiben von Absätzen durch ein KI-Modell inakzeptabel. Autoren müssen jede vorgeschlagene Nuance kritisch prüfen können. Die nahtlose Integration in bestehende Änderungsverfolgungs- und Revisionssysteme ist daher ein zentrales Qualitätsmerkmal moderner Autorentools.

---

## Integration in native Office-Änderungsverfolgung (Track Changes)

Klassische Textverarbeitungsprogramme (wie ONLYOFFICE Desktop Editors oder LibreOffice Writer) besitzen hochdifferenzierte Revisionssysteme. Ein KI-Plugin darf den Textpuffer nicht destruktiv verändern, sondern muss seine Vorschläge als reguläre Revisionsereignisse einspeisen:

```
[Originaltext im Dokument]
"Die Ergebnisse sind ~~ziemlich gut~~ {++überzeugend++} und belegen den Effekt."
                         │
                         ├─ Rot/Durchgestrichen: Vorgeschlagene Löschung
                         └─ Grün/Unterstrichen: Vorgeschlagene Ergänzung
                                 │
                                 ▼
                     [Autorenentscheidung im UI]
                     [✓ Annehmen]   [✗ Ablehnen]
```

### Vorteile der Revisionsintegration:
1. **Selektive Übernahme:** Der Autor kann den Vorschlag der KI ganzheitlich annehmen, ihn satzweise ablehnen oder einzelne Wörter manuell anpassen.
2. **Autorenschafts-Transparenz:** Im Revisions-Metadatenfeld wird die Änderung mit der Kennzeichnung `Autor: KI-Assistent` und dem genauen Zeitstempel versehen. Dies schafft Rechtssicherheit bei urheberrechtlich relevanten Werken.
3. **Kommentar-Modus:** Anstatt den Text direkt zu modifizieren, kann das KI-SDK auch instruiert werden, didaktische oder stilistische Randnotizen (Comments) an zweifelhaften Passagen zu hinterlassen (*„Hinweis: Dieser Satz ist mit 42 Wörtern sehr lang und enthält drei Schachtelungen.“*).

---

## Revisionsformate für Markdown (CriticMarkup)

In dateibasierten Autorentools und Markdown-Editoren steht keine binäre Word-Revisionsverfolgung zur Verfügung. Hier hat sich der offene Standard **CriticMarkup** etabliert:

* **Ergänzungen:** `{++Dieser Text wurde von der KI ergänzt.++}`
* **Löschungen:** `{--Dieser überflüssige Satz entfällt.--}`
* **Ersetzungen:** `{~~alte Formulierung~>präzise Formulierung~~}`
* **Kommentare:** `{>>Hinweis: Quelle für diese Zahl belegen.<<}`

Ein KI-Plugin für Editoren wie Obsidian oder Typora generiert CriticMarkup-Tags, die vom Editor visuell als farbige Einschübe gerendert und per Tastenkombination angenommen oder verworfen werden können.

---

## Kopplung mit deterministischer Stilprüfung (Styleguides)

Generative Modelle neigen zu geschwätzigen Formulierungen und Phrasendrescherei. Um einen konsistenten redaktionellen Standard zu wahren, wird das KI-Framework-SDK mit deterministischen Stilprüfern (wie Vale oder LanguageTool) gekoppelt:

1. **Erkennung von Stilverstößen:** Der Linter analysiert das Dokument anhand konfigurierter Styleguides (z. B. Vermeidung von Passivkonstruktionen, Einhaltung von Corporate-Wording, Erkennung von Füllwörtern).
2. **Gezielte Korrekturaufforderung:** Findet der Linter einen Verstoß, übergibt das Tool dem KI-SDK die exakte Regelverletzung zusammen mit dem betroffenen Satz: *„Formuliere folgenden Satz im Aktiv um, ohne Fachbegriffe zu verändern.“*
3. **Ergebnisprüfung:** Der umformulierte Satz wird vor dem Einfügen erneut durch den Linter validiert. Erst bei Regelkonformität wird der Textvorschlag im Revisionsmodus angezeigt.

---

> [!NOTE]
> Wie Autoren ihre Manuskripte vor unerwünschtem Datenabfluss an externe Modellbetreiber schützen können, behandelt die Unterkategorie [Vertraulichkeit, Manuskriptschutz und lokale Inferenz](datensouveraenitaet-lokale-modelle.md).
