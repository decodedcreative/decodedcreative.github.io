# Session Storage

## What it is
A key-value store built into the browser (part of the Web Storage API) that persists data only for the lifetime of the current browser tab. Data survives page reloads within that tab but is cleared as soon as the tab is closed, and it isn't shared with other tabs — even ones on the same origin.

## Why it's useful
- Gives you a scratchpad for state that should only live as long as the current tab/session.
- Same simple synchronous API as local storage, so it's easy to reach for.
- Naturally isolates state per tab, which avoids cross-tab interference for transient data.

## Classic use-cases
- Multi-step forms/wizards where progress should survive a reload but not persist forever.
- Per-tab UI state (e.g., scroll position, expanded/collapsed panels, active filter selections).
- One-time flags, like "don't show this tooltip again this session" or tracking a single checkout flow.

## Pros
- Automatically cleaned up when the tab closes — no manual cleanup needed.
- Isolated per tab, so parallel tabs don't clobber each other's transient state.
- Same simple, synchronous API as local storage.
- Similar capacity to local storage (~5–10MB per origin).

## Cons
- Not shared across tabs, which is sometimes surprising (e.g., opening a link in a new tab loses the state).
- Synchronous API can block the main thread for large reads/writes.
- Not sent to the server automatically — must be read and transmitted manually if needed.
- Not encrypted — vulnerable to XSS just like local storage.
- Lost on tab close, so it's unsuitable for anything that needs to persist across visits.

## Interview questions
1. How does session storage's lifetime differ from local storage and cookies?
2. Why doesn't session storage share data between two tabs of the same site?
3. What happens to session storage data when a tab is duplicated vs. reopened after being closed?
4. When would you pick session storage over local storage for form/wizard state?
5. Is session storage safe for storing an auth token? Why or why not?
6. How would you detect that session storage is full or unavailable (e.g., private browsing restrictions)?
