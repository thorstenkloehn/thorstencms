# Notebooks und ausführbare Dokumente

[Übergeordnete Kategorie: Dokumentenerstellung, Wikis und Notebooks](../dokumentation.md)

Interaktive Arbeitsumgebungen und eng zugehörige Publishing-Systeme.

## Open-Source-Auswahl nach Reifegrad

**5 passende Einträge:** ausschließlich PostgreSQL oder Inhaltsdateien.
Die Auswahl enthält genau fünf passende Projekte, nach Reifegrad priorisiert.

Stand: **26. September 2026**. Redaktionelle Auswahl aus geprüften Projekten;
[Bewertungskriterien und Grenzen](../software.md) gelten auch hier.
Die Rangfolge priorisiert Reife und danach die Passung zum Thema.

| Rang | Software und offizielle Quelle | Lizenz des betrachteten Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [JupyterLab](https://github.com/jupyterlab/jupyterlab) | BSD-3-Clause | Sehr hoch | Etabliertes Notebook-Ökosystem mit Dokumentation. | Dateien: [Notebook-Dateien (.ipynb)](https://github.com/jupyterlab/jupyterlab) |
| 2 | [Jupyter Notebook](https://github.com/jupyter/notebook) | BSD-3-Clause | Sehr hoch | Dokumentierte Wartung und Upgrade-Hinweise im Jupyter-Projekt. | Dateien: [Notebook-Dateien (.ipynb)](https://github.com/jupyter/notebook) |
| 3 | [R Markdown](https://github.com/rstudio/rmarkdown) | MIT | Sehr hoch | Etabliertes R-Paket mit Dokumentation und Änderungsverlauf. | Dateien: [Rmd-Quellen und Ausgabedateien](https://github.com/rstudio/rmarkdown) |
| 4 | [nbconvert](https://github.com/jupyter/nbconvert) | BSD-3-Clause | Sehr hoch | Dokumentierter Jupyter-Baustein mit Release-Prozess. | Dateien: [Notebook-Dateien und Exporte](https://github.com/jupyter/nbconvert) |
| 5 | [Quarto](https://github.com/quarto-dev/quarto-cli) | MIT | Hoch | Dokumentiertes Projektmodell für Bücher und ausführbare Inhalte. | Dateien: [Markdown-/Notebook-Quellen und Ausgabedateien](https://github.com/quarto-dev/quarto-cli) |

## Einsatz und Abgrenzung

JupyterLab und Notebook sind Anwendungen. R Markdown und Quarto verbinden Text mit Berechnungen; nbconvert übernimmt die Ausgabe und ist kein Editor.

- **JupyterLab:** Reproduzierbare Ausführung hängt zusätzlich von Kerneln und Abhängigkeiten ab.
- **Jupyter Notebook:** Erweiterungen sind nicht über alle Hauptversionen kompatibel.
- **R Markdown:** Schwerpunkt auf R; Abhängigkeiten gehören zum Dokument.
- **nbconvert:** Keine eigenständige Oberfläche zur gemeinsamen Redaktion.
- **Quarto:** Codeausführung benötigt passende Laufzeitumgebungen.
