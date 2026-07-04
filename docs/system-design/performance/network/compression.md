# Compression (Gzip/Brotli)

## What it is
Server-side compression of text-based HTTP responses (HTML, CSS, JS, JSON) before sending them over the network, with the browser decompressing on arrival. Gzip is the long-standing standard; Brotli is a newer algorithm that generally achieves smaller output, especially at higher compression levels.

## Why it's useful
- Text-based assets compress extremely well (often 60-80% smaller), directly cutting transfer time.
- Nearly free to enable — supported by virtually all browsers and most servers/CDNs out of the box.
- Brotli in particular can meaningfully reduce JS/CSS bundle transfer size beyond what Gzip achieves.

## Classic use-cases
- Compressing JS/CSS bundles and API JSON responses as a default part of server/CDN configuration.
- Pre-compressing static assets at build time (rather than compressing on every request) to avoid repeated CPU cost.
- Any production web server serving text-based content — this is close to a mandatory baseline optimization.

## Pros
- Large, consistent size reduction for text-based content with minimal implementation effort.
- Well-standardized (`Content-Encoding` header) and broadly supported.
- Brotli's static/pre-compressed mode achieves strong ratios with no runtime CPU cost.

## Cons
- Compressing on every request (rather than pre-compressing static files) adds CPU overhead at serve time.
- Doesn't help already-compressed formats (images like JPEG, video) — compression only meaningfully helps text-based assets.
- Very high compression levels trade CPU time for size, which matters for dynamically generated (non-cacheable) responses.

## Interview questions
1. Why does compressing JSON/JS/CSS work so well compared to compressing an already-compressed image format?
2. What's the practical difference between Gzip and Brotli in terms of compression ratio and CPU cost?
3. What's the tradeoff between pre-compressing static assets at build time vs. compressing dynamically per request?
4. How does a browser know a response is compressed, and what header communicates the encoding used?
5. Would you increase compression level for a highly dynamic, uncacheable API response? Why or why not?
