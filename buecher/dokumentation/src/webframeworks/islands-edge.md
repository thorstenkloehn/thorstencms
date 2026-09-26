# Server Components, Islands und Edge

[Übergeordnete Kategorie: Webframeworks](../webframeworks.md)

Diese Ansätze begrenzen die im Browser ausgeführte Arbeit oder verteilen die Ausführung. Server Components, Islands und Resumability sind unterschiedliche Techniken.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**. [Bewertungskriterien und Grenzen](../software.md).

| Rang | Software und offizielle Quelle | Lizenz des Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Next.js](https://github.com/vercel/next.js) | MIT | Hoch | Breites React-Ökosystem mit dokumentierten Server- und Client-Komponenten. | Dateien: [Markdown-/MDX-Inhalte](https://nextjs.org/docs/app/guides/mdx) |
| 2 | [Astro](https://github.com/withastro/astro) | MIT | Hoch | Dokumentation, Sicherheitsrichtlinie und offene Governance. | Dateien: [Markdown-/MDX-Dateien und Komponenten](https://github.com/withastro/astro) |
| 3 | [Qwik](https://github.com/QwikDev/qwik) | MIT | Hoch | Dokumentiertes Resumability-Modell; Auswahl bezieht sich auf die stabile Linie. | Dateien: [Markdown-/MDX-Seiten](https://qwik.dev/docs/guides/mdx/) |
| 4 | [Fresh](https://github.com/freshframework/fresh) | MIT | Hoch | Dokumentierte Islands-Architektur auf Deno. | PostgreSQL: eigene serverseitige Anbindung über [Deno-PostgreSQL-Treiber](https://docs.deno.com/examples/postgres/) |
| 5 | [SolidStart](https://github.com/solidjs/solid-start) | MIT | Mittel | Dokumentiertes Full-Stack-System mit kürzerer Langzeiterfahrung. | PostgreSQL: serverseitig in Node.js über [node-postgres](https://node-postgres.com/); eigene Integration erforderlich |

## Einsatz und Abgrenzung

Fresh wird mit Deno und PostgreSQL, SolidStart mit Node.js und PostgreSQL betrachtet. Die Datenbanktreiber müssen in serverseitigen Routen eingebunden werden. Diese Auswahl garantiert keine Ausführbarkeit auf jeder Edge-Plattform. Qwik bezeichnet hier die stabile Version, nicht die angekündigte Beta der nächsten Hauptversion.
