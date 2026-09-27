# Git-Workflows, Pull Requests und Diff-Prüfung

[Übergeordnete Kategorie: Docs-as-Code und KI-Framework-SDKs](../docs-as-code-ki-integration.md)

Die Stärke von Docs-as-Code liegt in der Verwendung von Git als unveränderlicher Versionshistorie. Jede Textänderung ist einer Person oder einem Bot zugeordnet, kann bis zum einzelnen Zeichen nachverfolgt und im Fehlerfall mit einem einzigen Befehl (`git revert`) zurückgerollt werden.

---

## Das Pull-Request-Muster für KI-Agenten

Wird ein KI-Framework-SDK in ein Dokumentations-Repository integriert, muss es sich denselben Governance-Regeln unterwerfen wie menschliche Entwickler. Der Ablauf folgt einem strikten Branching-Muster:

```
[Auslöser: Neuer Release oder Dokumentationsaufgabe]
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│ 1. Isolierter Arbeitszweig (Branching)                      │
│    `git checkout -b docs/ai-update-oauth-guide`             │
└────────────────────────┬────────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────────┐
│ 2. Gezielte Datei-Modifikation                              │
│    KI-SDK ändert ausschließlich betroffene Markdown-Dateien │
└────────────────────────┬────────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────────┐
│ 3. Atomarer Commit mit nachvollziehbarer Signatur           │
│    `git commit -m "docs: OAuth2 PKCE-Ablauf aktualisiert"`  │
└────────────────────────┬────────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────────┐
│ 4. Erstellung des Pull Requests (PR)                        │
│    ├─ Strukturierte PR-Beschreibung mit Änderungsgrund      │
│    ├─ Kennzeichnung mit Label `ai-generated`                │
│    └─ Verlinkung zu betroffenen Quellcode-Dateien           │
└────────────────────────┬────────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────────┐
│ 5. Merge-Gate: Prüfung durch menschlichen Maintainer        │
│    Freigabe und automatischer Merge erst nach Bestätigung   │
└─────────────────────────────────────────────────────────────┘
```

---

## Diff-Prüfung und Review-Effizienz

In einem CMS muss ein Redakteur oft den gesamten Artikel erneut lesen, um festzustellen, was sich geändert hat. In Git reduziert sich die kognitive Last auf die **Delta-Prüfung (Diff)**:

* **Fokussierte Zeilenansicht:** Der Reviewer sieht im GitHub- oder GitLab-Interface präzise, welche Absätze gestrichen (rot) und welche neu hinzugefügt (grün) wurden.
* **Erkennung von „Scope Creep“:** Versucht das Sprachmodell über die eigentliche Aufgabenstellung hinaus ungefragt andere Kapitel umzuformulieren, wird dies im Pull Request sofort als unzulässige Dateiänderung sichtbar und kann zurückgewiesen werden.
* **Review-Kommentare auf Zeilenebene:** Menschliche Autoren können direkt an der problematischen Zeile Feedback hinterlassen (z. B. *„Fachbegriff unpräzise“*), das vom KI-SDK in einem Folge-Commit verarbeitet werden kann.

---

## Technische Schutzmaßnahmen für Repositories

Um die Integrität des Dokumentationsbestands sicherzustellen, müssen im Git-Server klare Schutzregeln (Branch Protection Rules) konfiguriert sein:

1. **Kein Push auf Hauptzweige:** Das Konto des KI-Bots besitzt keine Schreibberechtigung auf `main` oder `release`-Branches. Jeder Versuch führt zu einem Zugriffsfehler.
2. **Erforderliche Status-Checks (Required Checks):** Ein Pull Request kann erst dann zusammengeführt werden, wenn alle CI-Pipelines (Build, Linter, Link-Checker) erfolgreich abgeschlossen wurden.
3. **Erforderliche Genehmigungen (Required Approvals):** Mindestens ein namentlich autorisierter menschlicher Maintainer muss den PR explizit absegnen.
4. **Keine Force-Pushes:** Befehle wie `git push --force` müssen für automatisierte Bot-Konten serverseitig vollständig gesperrt sein, um das versehentliche Überschreiben von Versionshistorien auszuschließen.

---

> [!NOTE]
> Welche automatisierten Prüfungen in der CI-Pipeline vor dem Review stattfinden müssen, erläutert die Unterkategorie [CI/CD-Pipelines, Linter-Schleifen und Build-Prüfung](ci-cd-linter-schleifen.md).
