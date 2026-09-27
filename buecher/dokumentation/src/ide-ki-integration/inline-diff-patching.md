# In-Editor-Diffs, AST-Patching und Puffer-Synchronisation

[Übergeordnete Kategorie: IDEs, Code-Editoren und KI-Framework-SDKs](../ide-ki-integration.md)

Eine zentrale architektonische Herausforderung bei der IDE-Integration ist die Art und Weise, wie Code-Modifikationen in den aktiven Editor-Puffer übertragen werden. Wenn ein Sprachmodell für eine dreizeilige Änderung eine 1.500 Zeilen lange Quellcodedatei komplett neu generiert, führt dies zu untragbaren Latenzen, hohen Tokenkosten und gefährlichen Auslassungsfehlern (wie dem berüchtigten Kommentar `// ... rest of code remains unchanged ...`).

---

## Patching-Strategien: Search-and-Replace vs. AST-Replacement

Um Änderungen schnell und minimalinvasiv durchzuführen, setzen moderne KI-Plugins auf zwei primäre Patch-Verfahren:

```
Verfahren 1: Search-and-Replace-Blöcke (Textuell / Zeilenbasiert)
<<<<<<< SEARCH
def authenticate(token: str) -> bool:
    return token == "secret"
=======
def authenticate(token: str) -> bool:
    return hmac.compare_digest(token, SECRET_KEY)
>>>>>>> REPLACE

Verfahren 2: AST-Node-Replacement (Syntaktisch über Tree-sitter)
[Tree-sitter identifiziert AST-Knoten: `FunctionDeclaration (name='authenticate')`]
              │
              ▼ Knoten im Syntaxbaum gezielt austauschen
[Editor ersetzt exakt den Sub-Tree; benachbarte Funktionen bleiben unberührt]
```

### 1. Search-and-Replace-Blöcke
Das Modell wird instruiert, ausschließlich den unveränderten Originalblock (`SEARCH`) und den gewünschten neuen Code (`REPLACE`) auszugeben.
* **Vorteile:** Minimaler Token-Verbrauch, universell in fast allen Programmiersprachen anwendbar.
* **Herausforderung:** Der `SEARCH`-Block muss genügend Kontextzeilen enthalten, um innerhalb der Datei eindeutig lokalisierbar zu sein.

### 2. Syntaktisches AST-Node-Replacement
Über Tree-sitter lokalisiert der Editor die genauen Start- und End-Bytes der zu ändernden Funktion oder Klasse.
* **Vorteile:** Resistent gegen Formatierungsabweichungen (z. B. Einrückungsunterschiede zwischen Tabs und Spaces). Selbst wenn sich die Zeilennummern durch vorangegangene Änderungen verschoben haben, bleibt der AST-Knoten über seinen Symbolnamen eindeutig adressierbar.

---

## Interaktive Inline-Diff-Darstellung im Editor

Erfahrene Entwickler akzeptieren selten maschinelle Code-Änderungen ungeprüft. Die Darstellung muss sich daher nahtlos in das visuelle Feedback der IDE einfügen:

1. **Farbliche Inline-Gegenüberstellung:** Im aktiven Editor-Puffer wird der Originalcode rot hervorgehoben (oder ausgegraut), während der vorgeschlagene neue Code unmittelbar darunter in grünem Hintergrund gerendert wird.
2. **Tastaturgesteuertes Chunker-Management:**
   * `Strg + Y` / `Alt + Enter`: Akzeptiert den vorgeschlagenen Code-Block und entfernt den alten Code.
   * `Strg + N` / `Alt + Backspace`: Verwirft den Vorschlag und stellt den Originalzustand wieder her.
   * **Partielle Akzeptanz:** Entwickler können einzelne Zeilen des KI-Vorschlags manuell editieren oder übernehmen, während der Rest verworfen wird.
3. **Schutz der Undo/Redo-Historie:** Die Anwendung von Diffs muss über die offiziellen Transaktions-APIs der Editoren erfolgen (z. B. `WorkspaceEdit` in VS Code/VSCodium oder `nvim_buf_set_text` in Neovim). Nur so bleibt die lokale Rückgängig-Funktion (`Strg + Z`) für den Entwickler uneingeschränkt erhalten.

---

## Puffer-Synchronisation und Konfliktbehandlung

Tippt ein Entwickler im Editor weiter, während das KI-SDK im Hintergrund einen Refactoring-Vorschlag berechnet, entsteht ein Synchronisationskonflikt:

* **Statisches Zeilen-Tracking:** Veralten Zeilennummern durch zwischenzeitliche Tastaturanschläge, schlägt ein naiver Zeilenpatch fehl.
* **Inkrementelle Puffer-Transformation:** Moderne Erweiterungen tracken jede Cursor- und Textänderung als Transformation. Trifft die Antwort des KI-SDKs ein, rechnet der Editor die relativen Verschiebungen automatisch in das Patch-Muster ein, bevor das Inline-Diff gerendert wird.

---

> [!NOTE]
> Wenn das KI-SDK nicht nur Code bearbeiten, sondern auch Compiler aufrufen und Tests ausführen soll, sind gesonderte Schutzvorkehrungen nötig. Diese werden im Abschnitt [Terminal-Schleifen, Test-Runner und Workspace-Sandboxing](terminal-agenten-sandboxing.md) behandelt.
