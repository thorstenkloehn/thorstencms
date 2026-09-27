# Streaming und Transportprotokolle

[Übergeordnete Kategorie: Webframeworks und KI-Framework-SDKs](../web-ki-integration.md)

Die schrittweise Übertragung generierter Text-Tokens vom Sprachmodell über das Webframework bis in den Browser ist entscheidend für eine reaktive Benutzeroberfläche. Während eine vollständige Antwort mehrere Sekunden oder Minuten beanspruchen kann, reduziert das Streaming die wahrgenommene Antwortzeit (Time to First Token) auf wenige hundert Millisekunden.

---

## Protokollvergleich für Modell-Datenströme

Für den Transport gestreamter Antworten stehen in modernen Webframeworks drei primäre Protokolle zur Verfügung:

| Kriterium | Server-Sent Events (SSE) | WebSockets | Web Streams API (Fetch Chunked) |
| :--- | :--- | :--- | :--- |
| **Richtung** | Unidirektional (Server zu Client) | Bidirektional (Full-Duplex) | Unidirektional (Server zu Client) |
| **Basisprotokoll** | Standard HTTP/1.1 oder HTTP/2 | TCP nach HTTP-Upgrade-Handshake | Standard HTTP/1.1 oder HTTP/2 |
| **Browser-Unterstützung** | Nativ über `EventSource` / Fetch | Nativ über `WebSocket`-API | Nativ über `ReadableStream` |
| **Proxy- & Firewall-Kompatibilität** | Sehr hoch; passiert Standard-Proxies | Mittel; erfordert Upgrade-Unterstützung | Sehr hoch |
| **Wiederverbindung** | Automatisch durch Browser spezifiziert | Muss manuell im Client implementiert werden | Manuell über Verbindungsabbruch-Handler |
| **Typischer Einsatzzweck** | Text-Chat, Code-Generierung, Markdown | Audio-/Sprachstreaming, Multi-User-Kollaboration | Moderne Fullstack- & Edge-Webframeworks |

### 1. Server-Sent Events (SSE)
SSE hat sich als Standard für die Ausgabe von Sprachmodell-Tokens durchgesetzt. Das Webframework sendet den Header `Content-Type: text/event-stream` und schaltet die HTTP-Pufferung ab (`X-Accel-Buffering: no` bei Nginx). Jeder Token-Chunk wird als standardisiertes Datenfeld formatiert:

```http
HTTP/1.1 200 OK
Content-Type: text/event-stream
Cache-Control: no-cache
Connection: keep-alive

data: {"token": "Die"}

data: {"token": " Architektur"}

data: [DONE]
```

### 2. Web Streams API und HTTP/2 Multiplexing
In modernen Laufzeiten (Node.js, Deno, Edge-Runtimes) nutzen Webframeworks die native `ReadableStream`-Schnittstelle. Hierbei werden Datenblöcke im binären oder UTF-8-Format über Standard-HTTP-Responses übertragen. Unter HTTP/2 oder HTTP/3 entfällt der frühere Verbindungsengpass (Head-of-Line Blocking), da viele parallele Datenströme über eine einzige TCP/QUIC-Verbindung gemultiplext werden.

---

## Backpressure und Pufferverwaltung

Wenn ein Sprachmodell schneller Tokens liefert, als der Client diese über eine mobile oder instabile Internetverbindung abrufen kann, entsteht ein Rückstau (Backpressure).

* **Gefahr:** Puffert das Webframework alle auflaufenden Tokens unbegrenzt im Arbeitsspeicher, führt eine hohe Zahl gleichzeitiger Stream-Verbindungen schnell zur Erschöpfung des RAMs (Memory Exhaustion).
* **Lösung:** Moderne asynchrone Controller (z. B. in FastAPI, Spring WebFlux oder Node.js Streams) nutzen nicht-blockierende Warteschlangen mit begrenzter Puffergröße (Bounded Queues). Meldet die zugrunde liegende TCP-Schicht einen vollen Sendepuffer, pausiert das Webframework das Auslesen der nächsten Chunks aus dem KI-SDK, bis der Client wieder Daten empfangen hat.

---

## Verbindungsabbruch und Kostenkontrolle

Ein kritischer Aspekt bei der Integration von KI-SDKs in Webframeworks ist die Weiterleitung von Abbruchsignalen. Wenn ein Nutzer den Browser schließt, auf „Abbrechen“ klickt oder die Seite verlässt, muss der serverseitige Modellaufruf sofort beendet werden.

```
[Browser schließt Tab]
         │ TCP FIN / RST
         ▼
[Webframework erkennt Client-Disconnect]
         │ AbortController / Cancellation Token
         ▼
[KI-Framework-SDK bricht HTTP-Stream ab]
         │ HTTP CANCEL / Connection Close
         ▼
[Modellanbieter stoppt Token-Erzeugung & Abrechnung]
```

### Implementierungsregeln für Webframeworks:
1. **Prüfung auf Verbindungsabbruch:** Der Stream-Generator muss in jeder Iteration prüfen, ob die Client-Verbindung noch besteht (z. B. `await request.is_disconnected()` in FastAPI oder Prüfung von `req.signal.aborted` in Node.js).
2. **Signal-Kopplung:** Das Abbruchsignal des Web-Requests muss direkt an den Aufruf des KI-SDKs übergeben werden (z. B. via `AbortSignal`).
3. **Kostenvermeidung:** Ohne diese Kopplung läuft die Inferenz beim Cloud-Provider bis zum konfigurierten Token-Limit weiter. Dies verursacht unnötige API-Kosten und bindet serverseitige Ressourcen.

---

> [!NOTE]
> Die Einbindung asynchroner Hintergrund-Aufgaben bei nicht-streamenden Prozessen wird im folgenden Abschnitt [Asynchrone Workflows, Queues und Persistenz](workflows-persistenz.md) erläutert.
