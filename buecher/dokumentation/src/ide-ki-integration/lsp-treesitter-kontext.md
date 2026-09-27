# LSP, Tree-sitter und symbolbewusste Kontextanalyse

[Übergeordnete Kategorie: IDEs, Code-Editoren und KI-Framework-SDKs](../ide-ki-integration.md)

In großen Software-Repositories scheitert naive Volltext- oder Vektorsuche häufig an der Eigenart von Programmiersprachen. Wird im Code `user.calculate_discount()` aufgerufen, nützen zehn ähnliche Textfragmente aus anderen Klassen wenig. Das Sprachmodell benötigt zwingend die exakte Schnittstellendefinition der Methode und den zugehörigen Typ von `user`.

Die Kopplung von KI-Framework-SDKs an das **Language Server Protocol (LSP)** und Syntax-Parser wie **Tree-sitter** verwandelt unstrukturierten Text in semantisch navigierbaren Code.

---

## Das Language Server Protocol als semantische Brücke

Das von Microsoft initiierte Language Server Protocol (LSP) standardisiert die Kommunikation zwischen Editoren und compilerspezifischen Sprachservern (wie `rust-analyzer`, `pyright`, `gopls` oder `typescript-language-server`). Anstatt eigene Code-Parser zu implementieren, nutzt das KI-Plugin die bestehende LSP-Infrastruktur der IDE:

```
[Entwickler markiert Methodenaufruf im Editor]
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│ 1. Editor sendet LSP-Anfragen an Sprachserver               │
│    ├─ `textDocument/definition` (Wo ist die Methode definiert?)
│    ├─ `textDocument/typeDefinition` (Welcher Typ ist `user`?)│
│    └─ `textDocument/publishDiagnostics` (Aktive Compiler-Warnungen)
└────────────────────────┬────────────────────────────────────┘
                         │ Exakte Code-Definitionen & Typen
┌────────────────────────▼────────────────────────────────────┐
│ 2. Kontext-Assembler des KI-SDKs                            │
│    Fügt Typ-Definitionen + Compiler-Fehler in Prompt ein    │
└────────────────────────┬────────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────────┐
│ 3. Sprachmodell generiert typsicheren Code                  │
│    Erfüllt Compiler-Garantien ohne Typ-Halluzinationen      │
└─────────────────────────────────────────────────────────────┘
```

### Die wichtigsten LSP-Methoden für KI-Assistenten:
* `textDocument/definition`: Findet die exakte Deklaration einer Funktion oder Klasse über Modul- und Package-Grenzen hinweg.
* `textDocument/references`: Findet alle Stellen im Projekt, an denen eine Funktion aufgerufen wird. Dies erlaubt dem KI-SDK abzuschätzen, ob ein Refactoring kollaterale Fehler in anderen Dateien erzeugt.
* `textDocument/publishDiagnostics`: Übergibt aktive Fehlermeldungen (z. B. fehlende Typ-Konvertierung in Zeile 84) direkt als Fehlersignal an das KI-SDK. Das Modell muss den Fehler nicht erraten, sondern erhält die offizielle Compiler-Meldung.

---

## Tree-sitter für Scope-Erkennung und Code-Skelette

Während LSP für die dateiübergreifende Symbolauflösung zuständig ist, liefert **Tree-sitter** inkrementelle, extrem schnelle Syntaxbäume (AST) direkt im Editor:

1. **Präzise Scope-Erkennung:** Tree-sitter ermittelt sofort, in welchem Gültigkeitsbereich sich der Cursor befindet (z. B. *„In Methode `handle_request`, innerhalb von `match`-Block, 2. Verschachtelungsebene“*). Dies verhindert, dass das Modell Code generiert, der lokale Variablen überschreibt.
2. **Context Pruning über Code-Skelette (Skeletonization):** Um das Kontextfenster des Modells optimal zu nutzen, müssen nicht alle Dateien vollständig übertragen werden. Tree-sitter extrahiert die Struktur einer Datei (Klassen, Methodensignaturen, Typ-Annotationen, Docstrings), ersetzt jedoch deren Rumpf durch Platzhalter (`// ... implementation ...`). Das Modell versteht das gesamte Modul, ohne unnötige Implementierungs-Tokens zu verbrauchen.

---

## Der Qualitätsunterschied: Vorher und Nachher

| Kriterium | Naive Prompting-Ansätze (Grep / Textsuche) | Symbolbewusstes LSP- & Tree-sitter-Prompting |
| :--- | :--- | :--- |
| **Typensicherheit** | Erfindet oft plausible, aber nicht existierende Methoden | Nutzt verifizierte Typen und Signaturen des Sprachservers |
| **Token-Effizienz** | Überträgt ganze Dateien unkomprimiert | Komprimiert Module zu schlanken AST-Skeletten |
| **Fehlerkorrektur** | Vermutet Probleme anhand von Symptomen | Kennt die exakte Fehlermeldung des Compilers mit Zeilennummer |
| **Import-Management** | Vergisst oft erforderliche Modul-Imports | Ermittelt über LSP exakt die zu importierenden Namensräume |

---

> [!NOTE]
> Wie die so erzeugten Codeänderungen ohne Beschädigung benachbarter Zeilen in den Editor-Puffer übertragen werden, zeigt der Abschnitt [In-Editor-Diffs, AST-Patching und Puffer-Synchronisation](inline-diff-patching.md).
