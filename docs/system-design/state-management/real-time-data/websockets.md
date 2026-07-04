# WebSockets (Socket.IO)

## What it is
WebSockets provide a persistent, full-duplex TCP connection between client and server, allowing either side to send messages at any time after the initial HTTP handshake upgrades the connection. Socket.IO is a popular library built on top of WebSockets (with automatic fallback to HTTP long-polling) that adds features like automatic reconnection, rooms/namespaces, and acknowledgements.

## Why it's useful
- Enables true bidirectional communication — the server can push data to the client without the client having to ask first.
- A single long-lived connection avoids the overhead of repeatedly opening new HTTP connections for frequent updates.
- Socket.IO specifically smooths over browser/network inconsistencies with automatic reconnection and transport fallback.

## Classic use-cases
- Chat applications and live collaboration tools (cursors, shared documents).
- Real-time multiplayer games or live dashboards with frequent bidirectional updates.
- Live notifications where the client also needs to send frequent events back (e.g., typing indicators, presence).

## Pros
- True bidirectional, low-latency communication over a single persistent connection.
- Socket.IO adds reconnection, rooms/namespaces, and fallback transports on top of raw WebSockets, reducing boilerplate.
- Well suited for high-frequency, two-way interaction patterns that HTTP polling handles poorly.

## Cons
- Requires a persistent connection per client, which has different scaling characteristics than stateless HTTP requests (needs sticky sessions or a shared pub/sub layer like Redis across server instances).
- More complex infrastructure than request/response APIs — load balancers, proxies, and firewalls need WebSocket support configured correctly.
- Socket.IO's protocol is not plain WebSockets — a Socket.IO client can't talk to a raw WebSocket server and vice versa without compatibility layers.
- Overkill for cases where only the server needs to push data one-way (SSE is simpler for that).

## Interview questions
1. How does a WebSocket connection get established, and what does the HTTP upgrade handshake look like?
2. Why is scaling WebSocket servers horizontally harder than scaling stateless HTTP APIs? How would you solve it?
3. What does Socket.IO add on top of raw WebSockets, and why might you choose one over the other?
4. Compare WebSockets to Server-Sent Events — when would one-way SSE be sufficient instead of full-duplex WebSockets?
5. How do you handle authentication and reconnection for a WebSocket connection?
6. What happens to in-flight messages if a WebSocket connection drops, and how would you design for reliable delivery?
