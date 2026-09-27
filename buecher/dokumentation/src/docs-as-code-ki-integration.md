# Docs-as-Code und KI-Framework-SDKs

Der Docs-as-Code-Ansatz überträgt bewährte Methoden der Softwareentwicklung auf die Erstellung und Pflege von Dokumentationen: Texte werden in einfachen Auszeichnungssprachen (wie Markdown, AsciiDoc oder Org-Mode) verfasst, in Versionskontrollsystemen (Git) verwaltet, über Pull Requests begutachtet und durch automatisierte CI/CD-Pipelines zu fertigen Websites oder Handbüchern gebaut.

Während in CMS- oder Wissenssystemen relationale Datenbanken und Vektorspeicher im Mittelpunkt stehen, ist im Docs-as-Code-Paradigma das **Git-Repository der einzige verbindliche Speicherort (Single Source of Truth)**.

Die Integration von KI-Framework-SDKs in Docs-as-Code-Umgebungen verändert die Art und Weise, wie Dokumentation gepflegt wird:

* **Änderungen als Git-Diffs:** Ein KI-System modifiziert keine Datenbankzeilen, sondern erzeugt Branch-Commits, Pull Requests (PRs) oder Patch-Dateien. Jede Änderung ist im Versionsverlauf zeilenweise nachvollziehbar.
* **Deterministische Build-Prüfung:** Nach jedem maschinellen Eingriff muss die CI-Pipeline sicherstellen, dass der Dokumentationsgenerator (z. B. `mdbook build` oder Sphinx) fehlerfrei durchläuft und keine defekten Links entstanden sind.
* **Kopplung von Heuristik und Regelwerk:** Die kreative, heuristische Textgenerierung von Sprachmodellen wird mit deterministischen Lintern (wie Vale für Stil und Typografie) in einer iterativen Korrekturschleife verknüpft.

```
┌─────────────────────────────────────────────────────────────┐
│             Git-Repository (Markdown / Quellcode)           │
└──────────────────────────────┬──────────────────────────────┘
                               │ Git Checkout / Diff
┌──────────────────────────────▼──────────────────────────────┐
│ CI/CD-Runner / CLI-Agentur (GitHub Actions, GitLab CI, etc.)│
│  ├─ Git-Status & Drift-Analyse (Code vs. Doku)              │
│  ├─ KI-Framework-SDK: Textentwurf oder PR-Review            │
│  └─ Deterministische Validierung (mdbook, Vale, Linters)    │
└──────────────────────────────▲──────────────────────────────┘
                               │ Iterative Korrekturschleife
┌──────────────────────────────▼──────────────────────────────┐
│ Feedback-Schleife: Fehlermeldung zurück an KI-SDK           │
│  (z. B. "Link defekt in Zeile 42" -> Modell korrigiert Link)│
└──────────────────────────────┬──────────────────────────────┘
                               │ Bei fehlerfreiem Build
┌──────────────────────────────▼──────────────────────────────┐
│ Pull Request / Freigabe-Gate durch menschlichen Reviewer    │
└─────────────────────────────────────────────────────────────┘
```

---

## Kernprinzipien der Docs-as-Code-Integration

1. **Kein direkter Push auf den Hauptzweig:** Ein KI-SDK darf niemals direkt Schreibrechte auf geschützte Zweige (`main` / `master`) besitzen. Alle Änderungen müssen als isolierte Feature-Branches mit zugehörigen Pull Requests eingereicht werden.
2. **Der Build entscheidet über die Gültigkeit:** Sprachmodelle erzeugen gelegentlich syntaktisch unvollständige Tabellen, ungültige Frontmatter-Metadaten oder nicht auflösbare relative Pfade. Ein Vorschlag gilt erst dann als technisch valide, wenn der Dokumenten-Build fehlerfrei abschließt.
3. **Drift-Vermeidung:** Dokumentation veraltet am häufigsten, wenn Code geändert, die Dokumentation aber vergessen wird. KI-SDKs in CI-Pipelines können geänderten Code analysieren und fehlende Dokumentationsanpassungen proaktiv vorschlagen.

---

## Unterkategorien dieses Kapitels

Die konkreten Integrationsmuster gliedern sich in drei Schwerpunkte:

* [Git-Workflows, Pull Requests und Diff-Prüfung](docs-as-code-ki-integration/git-pr-automation.md): Branching-Strategien für KI-Agenten, Generierung verständlicher PR-Beschreibungen und automatisierte Review-Gates.
* [CI/CD-Pipelines, Linter-Schleifen und Build-Prüfung](docs-as-code-ki-integration/ci-cd-linter-schleifen.md): Das Zusammenspiel von Sprachmodellen mit deterministischen Werkzeugen (mdBook, Vale), automatisierte Selbstkorrektur und Link-Validierung.
* [Code-to-Docs-Synthese und Drift-Erkennung](docs-as-code-ki-integration/code-to-docs-drift.md): Erkennung von Dokumentationslücken bei Quellcode-Änderungen, Extraktion von API-Dokumentation aus Typsignaturen und automatisierte Changelog-Erstellung.

---

> [!NOTE]
> Die Einordnung autonomer Entwicklungsassistenten wie Aider oder Cline findet sich in den Abschnitten [Sprachmodelle in Docs-as-Code](sprachmodelle/docs-as-code.md) und [KI- und CLI-Coding-Agenten im Vergleich](cli-agenten.md).
