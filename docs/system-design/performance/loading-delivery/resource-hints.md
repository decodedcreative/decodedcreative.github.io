# Resource Hints (preload, prefetch, preconnect)

## What it is
HTML `<link>` hints that tell the browser about resources it will need before it would normally discover them, letting it start network work earlier. `preconnect` warms up a connection (DNS/TCP/TLS) to a domain ahead of time, `preload` fetches a resource needed for the current page with high priority, and `prefetch` fetches a resource likely needed for a future navigation at low priority.

## Why it's useful
- Removes otherwise-hidden latency: without hints, the browser only discovers a resource once it parses the HTML/CSS/JS that references it.
- `preconnect` eliminates DNS/TCP/TLS handshake time for critical third-party origins (fonts, APIs, CDNs).
- `prefetch` can make the *next* page feel instantaneous by fetching its assets while the user is still on the current page.

## Classic use-cases
- `preconnect` to a font CDN or API origin used immediately on page load.
- `preload` for a critical hero image or web font that would otherwise be discovered late (e.g., referenced only inside CSS).
- `prefetch` for the next likely page in a flow (e.g., checkout step 2) based on user behavior.

## Pros
- Cheap to add (a single `<link>` tag) for often-significant latency wins.
- Directly targets the "discovery latency" problem that's invisible without profiling a waterfall.
- `preconnect`/`preload` can meaningfully improve Core Web Vitals like LCP.

## Cons
- Overusing hints (preloading/preconnecting to everything) wastes bandwidth and can *hurt* performance by competing with genuinely critical requests.
- `prefetch` for a page the user never visits wastes data, which matters on constrained/mobile connections.
- Hints are advisory — browsers can deprioritize or ignore them under resource pressure, so they're not a guarantee.

## Interview questions
1. What's the difference between `preload`, `prefetch`, and `preconnect`, and when would you use each?
2. Why can preloading too many resources actually hurt page performance instead of helping it?
3. How would you decide which third-party origins deserve a `preconnect`?
4. How does `prefetch` interact with a user's data usage on mobile, and when might you avoid it?
5. How would you verify a resource hint is actually being honored by the browser rather than ignored?
