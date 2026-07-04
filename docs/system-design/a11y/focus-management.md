# Focus Management

## What it is
Deliberately controlling where keyboard focus goes as the UI changes — moving focus into a modal when it opens, trapping it inside the modal while open, and returning it to the triggering element when it closes, rather than letting focus land somewhere confusing or get lost entirely.

## Why it's useful
- Keyboard and screen reader users navigate primarily via focus — if focus isn't managed deliberately during dynamic UI changes, they can easily lose track of where they are on the page.
- Focus traps (keeping focus inside an open modal) prevent users from silently tabbing into content that's visually hidden behind an overlay.
- Restoring focus after closing a dialog/menu preserves the user's place in the page instead of dropping them back at the very top.

## Classic use-cases
- Modals/dialogs: moving focus in on open, trapping it inside while open, restoring it to the trigger element on close.
- Client-side route changes in SPAs: moving focus to the new page's main heading so screen reader users know navigation happened.
- Dropdown menus and comboboxes: managing focus movement between the trigger and menu items via arrow keys.

## Pros
- Directly prevents one of the most disorienting experiences for keyboard/screen-reader users: losing track of where focus is.
- A relatively small, well-defined set of patterns (modal focus trap, route-change focus, menu focus) covers most real-world cases.
- Libraries (Radix, React Aria) implement correct focus management out of the box, reducing the need to hand-roll it.

## Cons
- Manually implementing correct focus trapping/restoration is fiddly to get exactly right (edge cases: closing via Escape vs. an action button, nested dialogs).
- Client-side routed SPAs don't get free focus management the way full page loads do — it has to be deliberately implemented.
- Easy to overlook entirely if accessibility isn't tested with a keyboard/screen reader during development.

## Interview questions
1. Why does an SPA route change need explicit focus management that a traditional full-page navigation gets for free?
2. How would you implement a focus trap for a modal, and what happens if you get it wrong?
3. Where should focus go after closing a modal, and why does that matter for the user's sense of context?
4. What's the risk of not managing focus at all in a single-page application?
5. How would you test that focus management is working correctly without relying only on a screen reader?
