# Code-to-Docs-Synthese und Drift-Erkennung

[Übergeordnete Kategorie: Docs-as-Code und KI-Framework-SDKs](../docs-as-code-ki-integration.md)

Eine der größten Herausforderungen bei der Softwarepflege ist die schleichende Entkopplung zwischen Quellcode und Dokumentation (Documentation Drift). Entwickler modifizieren Funktionen, ergänzen Parameter oder ändern Konfigurationsoptionen, versäumen es jedoch im Alltagsgeschäft häufig, die zugehörigen Handbücher und API-Referenzen zeitgleich anzupassen.

---

## Automatisierte Drift-Erkennung in der CI/CD-Pipeline

Durch die Integration eines KI-Framework-SDKs in die Continuous-Integration-Pipeline lässt sich dieser Drift automatisiert erkennen und beheben:

```
[Entwickler öffnet Pull Request mit Code-Änderungen]
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│ 1. Git-Diff-Analyse im CI-Runner                            │
│    Ermittelt geänderte Signaturen, Parameter & Endpunkte    │
└────────────────────────┬────────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────────┐
│ 2. KI-gestützte Dokumentations-Suche                        │
│    SDK durchsucht Markdown-Bestand nach Bezügen zum Code    │
└────────────────────────┬────────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────────┐
│ 3. Diskrepanz-Prüfung (Drift Detection)                     │
│    Wurden Parameter geändert, die in der Doku fehlen?       │
└────────────────────────┬────────────────────────────────────┘
                         │
        ┌────────────────┴────────────────┐
        │ Dokumentation aktuell?          │
        ▼                                 ▼
  [Ja: Keine Aktion]             [Nein: Drift erkannt]
                                          │
                         ┌────────────────▼───────────────────┐
                         │ 4. Automatisierter Dokumenten-Patch│
                         │    ├─ Bot schlägt PR-Commit vor    │
                         │    └─ Aktualisiert Beispiel-Aufrufe│
                         └────────────────────────────────────┘
```

### Der Ablauf im Detail:
1. **Diff-Inspektion:** Bei jedem PR auf die Codebasis extrahiert ein Skript das semantische Quellcode-Diff (z. B. geänderte Funktionen in TypeScript, Python oder Rust).
2. **Querverweis-Suche:** Das KI-SDK sucht im Dokumentationsverzeichnis nach Passagen, die den geänderten Funktionsnamen oder den betreffenden API-Endpunkt beschreiben.
3. **Drift-Meldung:** Findet das SDK eine Dokumentationsstelle, die veraltete Parameter oder überholte Rückgabewerte aufführt, verfasst der Bot einen zielgerichteten Review-Kommentar im PR oder pusht direkt einen ergänzenden Commit mit den aktualisierten Textzeilen auf den Dokumentations-Branch.

---

## Code-to-Docs-Synthese: Vom Schema zum Tutorial

Neben der reinen Erkennung von Lücken können KI-SDKs hochwertige Dokumentationsteile direkt aus maschinenlesbaren Quellcode-Artefakten ableiten:

* **Typendefinitionen und Schemata:** OpenAPI-Spezifikationen, Protobuf-Dateien oder Pydantic-Modelle enthalten präzise Typeninformationen, sind für Menschen jedoch oft schwer lesbar. Ein KI-SDK synthetisiert daraus zusammenhängende Einführungstexte, erklärt typische Anwendungsfälle und weist auf Randbedingungen hin.
* **Generierung valider Code-Beispiele:** Das Modell erzeugt praxisnahe Verwendungsbeispiele in verschiedenen Programmiersprachen (z. B. Curl, Python, JavaScript), die die neuen Parameter demonstrieren.

---

## Automatisierte Release-Notes und Changelogs

Klassische Changelogs beschränken sich oft auf das bloße Auflisten technischer Git-Commit-Nachrichten, die für Anwender wenig Aussagekraft besitzen.

### Aufgaben des KI-SDKs beim Release:
1. **Filterung nach Conventional Commits:** Analyse aller Commits seit dem letzten Release-Tag (`feat:`, `fix:`, `refactor:`, `perf:`).
2. **Synthese verständlicher Zusammenfassungen:** Das Modell fasst technische Änderungen aus der Anwenderperspektive zusammen (*„Was bedeutet diese Änderung für Nutzer der API?“*).
3. **Kategorisierung von Breaking Changes:** Kritische Änderungen mit Migrationsbedarf werden prominent hervorgehoben und mit Querverweisen auf die aktualisierten Dokumentationsabschnitte versehen.

---

> [!NOTE]
> Wie Dokumentationsänderungen über Git versioniert und gemeinsam mit Entwicklern begutachtet werden, vertieft das Hauptkapitel [Docs-as-Code: Änderungen gemeinsam prüfen](../docs-as-code.md).
