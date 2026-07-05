# HTTP/2

## What it is
The protocol version that introduced **multiplexing** — many requests and responses interleaved over a single TCP connection — replacing HTTP/1.1's model of one request per connection (or a handful of parallel connections as a workaround). It also added header compression (HPACK) and server push, solving HTTP/1.1's application-layer head-of-line blocking in the process.

## Why it's useful
- Multiplexing lets a browser fire off many requests over one connection instead of opening several parallel TCP connections (a common HTTP/1.1 workaround), reducing connection overhead.
- Header compression (HPACK) meaningfully reduces the repeated overhead of sending near-identical headers on every request.
- Solved head-of-line blocking *at the application layer* — HTTP/1.1 had to wait for one response before starting the next on the same connection; HTTP/2 interleaves them.

## Classic use-cases
- Any modern HTTPS website — HTTP/2 has been the practical default for years, requiring no special application code to benefit from it.
- Pages making many small requests (icons, scripts, API calls) that previously relied on domain sharding or bundling to work around HTTP/1.1's connection limits.
- Servers wanting to reduce connection overhead without applications needing to change how they make requests.

## Pros
- Multiplexing removes the need for HTTP/1.1-era workarounds like domain sharding or aggressive asset bundling just to parallelize requests.
- Header compression reduces bandwidth overhead, especially valuable for many small requests with repetitive headers (cookies, auth tokens).
- Transparent upgrade — existing HTTP semantics (methods, status codes, caching) are unchanged, so it required little to no application code changes to benefit.

## Cons
- Still runs over TCP, so a single lost packet stalls every multiplexed stream on that connection — the transport-layer head-of-line blocking problem HTTP/3 exists specifically to solve.
- Server push (an original HTTP/2 feature) saw limited real-world adoption and has since been deprecated in most browsers, having not delivered the expected benefit in practice.
- Some of the HTTP/1.1-era optimizations (domain sharding especially) can actually hurt performance under HTTP/2, requiring teams to unlearn old best practices.

## Interview questions
1. What is multiplexing in HTTP/2, and what problem did it solve compared to HTTP/1.1?
2. Why does a single dropped packet under HTTP/2 still stall multiple in-flight requests, despite multiplexing?
3. Why did HTTP/2 server push ultimately see limited adoption and get deprecated in most browsers?
4. Why can HTTP/1.1-era techniques like domain sharding actually hurt performance once a site moves to HTTP/2?
5. What specifically does HTTP/3 solve that HTTP/2 couldn't, given both support multiplexing?
