# Single-Page-Applications

[Übergeordnete Kategorie: Webframeworks](../webframeworks.md)

SPAs übernehmen große Teile der Darstellung und Navigation im Browser. Persistente Fachinformationen bleiben auf dem Server.

## Open-Source-Auswahl nach Reifegrad

**5 Einträge:** für den jeweils beschriebenen Speicherumfang ausgewählt.

Redaktioneller Stand: **27. September 2026**. [Bewertungskriterien und Grenzen](../software.md).

| Rang | Software und offizielle Quelle | Lizenz des Kerns | Reifegrad | Begründung | Passender Speicherweg und Nachweis |
| --- | --- | --- | --- | --- | --- |
| 1 | [React](https://github.com/facebook/react) | MIT | Sehr hoch | Etabliertes Komponentenökosystem; Routing und Datenzugriff ergänzen. | PostgreSQL über eigenes [Django-Backend](../webframeworks.md#speicherwege-fuer-webframeworks); [Frontend-Anbindung](https://react.dev/learn/build-a-react-app-from-scratch) |
| 2 | [Angular](https://github.com/angular/angular) | MIT | Sehr hoch | Integriertes Anwendungsframework mit dokumentiertem HTTP-Client. | PostgreSQL über eigenes [Django-Backend](../webframeworks.md#speicherwege-fuer-webframeworks); [Frontend-Anbindung](https://angular.dev/guide/http) |
| 3 | [Vue.js](https://github.com/vuejs/core) | MIT | Sehr hoch | Progressives Framework mit dokumentiertem Aufbau und Ökosystem. | PostgreSQL über eigenes [Django-Backend](../webframeworks.md#speicherwege-fuer-webframeworks); [Frontend-Anbindung](https://vuejs.org/guide/quick-start.html) |
| 4 | [Ember.js](https://github.com/emberjs/ember.js) | MIT | Sehr hoch | Langjähriges SPA-Framework mit Konventionen und Datenadaptern. | PostgreSQL über eigenes [Django-Backend](../webframeworks.md#speicherwege-fuer-webframeworks); [Frontend-Anbindung](https://guides.emberjs.com/release/models/) |
| 5 | [Svelte](https://github.com/sveltejs/svelte) | MIT | Hoch | Compilerorientierte Komponenten; für vollständige Anwendungen SvelteKit ergänzen. | PostgreSQL über eigenes [Django-Backend](../webframeworks.md#speicherwege-fuer-webframeworks); [Frontend-Anbindung](https://svelte.dev/docs/svelte/overview) |

## Einsatz und Abgrenzung

Die ausgewählte Betriebsvariante verwendet für jedes Frontend eine eigene HTTP-API mit Django REST framework und PostgreSQL. Das ist ein Architekturvorschlag, kein eingebauter PostgreSQL-Treiber des Frontends. Ember benötigt einen passenden API-Adapter beziehungsweise ein abgestimmtes Antwortformat.
