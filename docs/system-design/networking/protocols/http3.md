# HTTP/3

## What it is
The latest major HTTP protocol version, built on top of QUIC (a transport protocol running over UDP) instead of TCP. Its headline change is solving **head-of-line blocking at the transport layer**: in HTTP/2, a single lost TCP packet stalls every multiplexed stream sharing that connection, even ones unrelated to the lost packet; QUIC gives each stream independent delivery, so one dropped packet only stalls the stream it belongs to.

## Why it's useful
- Eliminates transport-level head-of-line blocking, which was the one problem HTTP/2's multiplexing couldn't solve on its own (HTTP/2 fixed head-of-line blocking at the application layer, but TCP itself still serialized delivery).
- QUIC's connection setup combines the transport and TLS handshake into fewer round trips, reducing connection latency — especially valuable on high-latency mobile networks.
- Connections survive network changes (e.g., switching from WiFi to cellular) because QUIC identifies connections by a connection ID rather than the traditional IP/port tuple, avoiding a full reconnect.

## Classic use-cases
- High-latency or lossy networks (mobile, satellite) where TCP's head-of-line blocking and handshake overhead cost the most.
- Any CDN/edge-served traffic where connection setup time is a meaningful fraction of total request time.
- Apps with many concurrent requests over one connection, where a single dropped packet under HTTP/2 would otherwise stall unrelated in-flight requests.

## Pros
- Solves transport-level head-of-line blocking, the core limitation HTTP/2 couldn't address.
- Faster connection establishment thanks to combined transport + TLS handshake.
- Resilient to network changes (WiFi ↔ cellular) without a full reconnection.

## Cons
- Running over UDP means some restrictive corporate/network firewalls block or throttle it, requiring fallback to HTTP/2.
- QUIC implementations are newer and less battle-tested than decades-old TCP, though this gap is closing quickly.
- Server/infrastructure support still varies — not every CDN or hosting platform has full HTTP/3 support enabled by default.

## Interview questions
1. What is head-of-line blocking, and how does it differ between HTTP/1.1, HTTP/2, and HTTP/3?
2. Why does HTTP/3 use QUIC over UDP instead of building directly on TCP?
3. How does QUIC's connection ID help with network changes like switching from WiFi to cellular?
4. What's a real-world scenario where HTTP/3's benefits matter most, and one where they matter least?
5. Why might a client or server fall back to HTTP/2 even when HTTP/3 is available?
