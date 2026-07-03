# Local Storage

## What it is
A key-value store built into the browser (part of the Web Storage API) that persists data on the client with no expiration date. Data survives page reloads, browser restarts, and even system reboots — it's only cleared when explicitly removed by the app or the user (e.g., clearing browser data).

## Why it's useful
- Lets the client remember state across sessions without hitting the server.
- Simple synchronous API (`localStorage.setItem/getItem/removeItem`) with no dependencies.
- Reduces server load and network requests for data that doesn't need to live in a database.

## Classic use-cases
- Persisting user preferences (theme, language, layout settings).
- Caching non-sensitive data to avoid refetching (e.g., draft form input, recently viewed items).
- Feature flags or A/B test bucket assignment that should persist across visits.

## Pros
- Persists indefinitely, across tabs and browser restarts.
- Simple, synchronous, well-supported API — no external library required.
- Shared across all tabs/windows of the same origin.
- Larger capacity than cookies (typically ~5–10MB per origin).

## Cons
- Synchronous API can block the main thread for large reads/writes.
- Not sent to the server automatically — must be read and transmitted manually if the backend needs it.
- Not encrypted — vulnerable to XSS (any injected script can read/write it).
- No expiration mechanism built in — stale data lingers unless the app manages cleanup.
- Same-origin only, so data doesn't transfer across subdomains without extra work.

## Interview questions
1. How does local storage differ from session storage and cookies in terms of lifetime and scope?
2. Why shouldn't you store sensitive data (tokens, PII) in local storage? What attack makes this risky?
3. Since local storage is synchronous, how could heavy use of it affect performance?
4. How would you keep local storage in sync across multiple open tabs?
5. What's the storage limit, and how would you handle exceeding it?
6. When would you choose local storage over IndexedDB?
7. How do you invalidate or version cached data in local storage when your app's data shape changes?
