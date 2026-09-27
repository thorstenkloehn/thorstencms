# CI/CD-Pipelines, Linter-Schleifen und Build-Prüfung

[Übergeordnete Kategorie: Docs-as-Code und KI-Framework-SDKs](../docs-as-code-ki-integration.md)

Sprachmodelle sind generative, stochastische Systeme. Sie können hochwertige Erklärungen formulieren, neigen jedoch gelegentlich zu formalen Fehlern: fehlerhafte Tabellensyntax, falsche relative Dateipfade, ungültige Frontmatter-Metadaten oder erfundene Markdown-Erweiterungen. Im Docs-as-Code-Ansatz werden diese Schwächen durch die Kopplung mit deterministischen Prüfwerkzeugen in CI/CD-Pipelines abgefangen.

---

## Die agentische Feedback- und Korrekturschleife

Anstatt fehlerhafte Entwürfe direkt dem Menschen vorzulegen, wird das KI-Framework-SDK in eine automatisierte Korrekturschleife eingebunden:

```
┌─────────────────────────────────────────────────────────────┐
│ 1. KI-Framework-SDK erzeugt Dokumenten-Entwurf             │
│    (z. B. Aktualisierung eines Handbuchkapitels)            │
└──────────────────────────────┬──────────────────────────────┘
                               │ Dateiänderung schreiben
┌──────────────────────────────▼──────────────────────────────┐
│ 2. Deterministische Test-Suite im CI-Runner                 │
│    ├─ Build-Test: `mdbook build` (Syntax, Struktur)         │
│    ├─ Link-Checker: Erkennung toter Links und 404-Pfade     │
│    ├─ Stil-Linter: `vale` (Terminologie, Tonfall)           │
│    └─ Markdown-Linter: `markdownlint` (Formatierung)        │
└──────────────────────────────┬──────────────────────────────┘
                               │
               ┌───────────────┴───────────────┐
               │ Build fehlgeschlagen?         │
               ▼                               ▼
       [Ja: Exit-Code > 0]             [Nein: Exit-Code = 0]
               │                               │
┌──────────────▼──────────────┐                ▼
│ 3. Fehler-Rückkopplung      │    ┌──────────────────────────┐
│    Fehlerausgabe & Zeilen   │    │ 4. PR freigeben / bereit │
│    an KI-SDK übergeben      │    │    zur menschlichen Sicht│
└──────────────┬──────────────┘    └──────────────────────────┘
               │ Gezielte Korrektur
               └───────────────► Zurück zu Schritt 1 (max. 3 Zyklen)
```

### Der iterative Ablauf:
1. **Ausführung der Linter-Suite:** Der CI-Runner prüft die geänderte Markdown-Datei mit statischen Prüfwerkzeugen.
2. **Kompilierung der Fehlermeldung:** Scheitert beispielsweise `mdbook build` an einem fehlerhaften Pfad (`"file not found: ../api/auth.md"`), fängt das Orchestrierungsskript die Standard-Fehlerausgabe (stderr) und die betroffene Zeilennummer ab.
3. **Selbstkorrektur-Prompt:** Das KI-SDK erhält den Auftrag: *„Der Build schlug mit folgendem Fehler fehl: [Fehlermeldung]. Korrigiere ausschließlich die beanstandete Zeile im Dokument.“*
4. **Erneuter Test:** Das Modell passt den Pfad an, und die CI-Suite prüft erneut. Erst wenn alle Tests ohne Warnungen und Fehler abschließen, wird die Bearbeitung beendet.

---

## Deterministische Prüfwerkzeuge im Überblick

Im Docs-as-Code-Stack übernehmen spezialisierte Open-Source-Werkzeuge die Qualitätsprüfung:

| Werkzeug | Prüfbereich | Typische abgefangene Fehler |
| :--- | :--- | :--- |
| **mdBook / Sphinx / MkDocs** | Compiler & Dokumentenstruktur | Ungültige Inhaltsverzeichnisse (`SUMMARY.md`), Syntaxfehler, fehlende Kapitel |
| **Vale** | Prosa, Terminologie & Stil | Verwendung veralteter Produktnamen, unzulässiges Passiv, Nichteinhaltung von Styleguides |
| **markdownlint** | Markdown-Syntax | Fehlende Leerzeilen um Code-Blöcke, uneinheitliche Überschriftenhierarchien, fehlerhafte Einrückungen |
| **Lychee / linkchecker** | Hyperlinks & Querverweise | Defekte interne relative Links, tote externe URLs (HTTP 404/500) |

---

## Der Nutzen für die Dokumentationsqualität

Durch die feste Kopplung generativer Modelle an deterministische Linter entsteht eine robuste Arbeitsteilung:
* Das **Sprachmodell** übernimmt die aufwendige Recherche, Formulierung und didaktische Aufbereitung von Texten.
* Der **Compiler** erzwingt unbestechlich formale Korrektheit, Link-Integrität und Regelkonformität.

Menschliche Reviewer müssen sich nicht mit Tippfehlern, defekten Links oder fehlerhafter Formatierung befassen, sondern können sich vollständig auf die inhaltliche Richtigkeit und Verständlichkeit konzentrieren.

---

> [!NOTE]
> Wie KI-SDKs genutzt werden können, um veraltete Dokumentation bei Code-Änderungen aufzuspüren, zeigt die Unterkategorie [Code-to-Docs-Synthese und Drift-Erkennung](code-to-docs-drift.md).
