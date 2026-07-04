# Service Workers & Offline Caching (PWA)

## What it is
A service worker is a script the browser runs in the background, separate from any page, that can intercept network requests and serve cached responses — enabling offline access and fine-grained caching strategies. It's a core building block of Progressive Web Apps (PWAs), alongside a web app manifest for installability.

## Why it's useful
- Lets an app work (fully or partially) without a network connection, by serving previously cached assets and data.
- Gives developers explicit control over caching strategy per request (cache-first, network-first, stale-while-revalidate), beyond what HTTP cache headers alone allow.
- Enables PWA features like installability, background sync, and push notifications.

## Classic use-cases
- Offline-capable web apps (note-taking, documentation sites, field-work tools) that must function with no connectivity.
- Instant repeat-load performance by serving the app shell from cache while revalidating in the background.
- Installable "app-like" experiences on mobile without going through a native app store.

## Pros
- Enables genuine offline functionality, which HTTP caching alone cannot provide.
- Fine-grained programmatic control over exactly what's cached and how staleness is handled.
- Can dramatically speed up repeat visits by serving the shell instantly from cache.

## Cons
- Adds real complexity: versioning caches, handling updates, and avoiding serving stale content indefinitely if not managed carefully.
- Debugging service worker lifecycle issues (installation, activation, stuck old versions) has a notorious learning curve.
- Not appropriate for every app — highly dynamic, always-online apps may get little benefit for the added complexity.

## Interview questions
1. How does a service worker intercept and respond to network requests?
2. What's the difference between cache-first, network-first, and stale-while-revalidate caching strategies?
3. How do you handle updating a service worker's cache without permanently serving stale content to returning users?
4. What is the service worker lifecycle (install, activate, fetch), and why does it sometimes get "stuck" on an old version?
5. What functionality does a service worker unlock that plain HTTP caching cannot provide?
