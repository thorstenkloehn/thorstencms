# Full-Stack- und Meta-Frameworks

[Übergeordnete Kategorie: Webframeworks](../webframeworks.md)

Meta-Frameworks verbinden Komponenten, Routing und serverseitige oder statische Seitenausgabe. Der Rendering-Modus wird passend zur Anwendung gewählt.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**. [Bewertungskriterien und Grenzen](../software.md).

| Rang | Software und offizielle Quelle | Lizenz des Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [Next.js](https://github.com/vercel/next.js) | MIT | Hoch | Breites React-Ökosystem mit dokumentierten Server- und Client-Komponenten. | Dateien: [Markdown-/MDX-Inhalte](https://nextjs.org/docs/app/guides/mdx) |
| 2 | [Nuxt](https://github.com/nuxt/nuxt) | MIT | Hoch | Dokumentiertes Vue-Meta-Framework mit Server-Routen. | PostgreSQL: serverseitig in Node.js über [node-postgres](https://node-postgres.com/); eigene Integration erforderlich |
| 3 | [SvelteKit](https://github.com/sveltejs/kit) | MIT | Hoch | Server-Rendering, Routing und statische Ausgabe im Svelte-Ökosystem. | PostgreSQL: serverseitig in Node.js über [node-postgres](https://node-postgres.com/); eigene Integration erforderlich |
| 4 | [Astro](https://github.com/withastro/astro) | MIT | Hoch | Dokumentation, Sicherheitsrichtlinie und offene Governance. | Dateien: [Markdown-/MDX-Dateien und Komponenten](https://github.com/withastro/astro) |
| 5 | [React Router](https://github.com/remix-run/react-router) | MIT | Hoch | Etabliertes Routing; Framework-Modus bündelt Datenladen und Rendering. | PostgreSQL: serverseitig in Node.js über [node-postgres](https://node-postgres.com/); eigene Integration erforderlich |

## Einsatz und Abgrenzung

Next.js und Astro sind hier für lokale Inhaltsdateien ausgewählt. Nuxt, SvelteKit und React Router werden als selbst gehostete Node.js-Anwendungen mit eigenem node-postgres-Datenzugriff betrachtet. Die Datenbankintegration ist Entwicklungsarbeit; ein statischer Export allein ersetzt keine Speicherung veränderlicher Nutzerdaten.
