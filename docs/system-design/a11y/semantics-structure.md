# Semantics + Structure

## What it is
Using HTML elements and ARIA attributes according to their intended meaning — `<button>` for buttons, `<nav>` for navigation, headings in a logical order — so that assistive technology (and the browser itself) can correctly understand what each part of a page is and how it's structured, rather than relying on visual styling alone to convey meaning.

## Why it's useful
- Semantic elements come with built-in behavior and accessibility for free (a `<button>` is focusable and keyboard-activatable by default; a `<div>` styled to look like one is not, unless you rebuild all that behavior manually).
- Screen readers use landmarks (`<nav>`, `<main>`, `<header>`) and heading structure to let users jump directly to the part of the page they care about, rather than reading everything linearly.
- ARIA fills gaps where native HTML has no equivalent (custom widgets like comboboxes or tab panels), but only when native elements genuinely can't express the structure.

## Classic use-cases
- Using real `<button>`/`<a>` elements instead of clickable `<div>`s, avoiding the need to manually reimplement keyboard and focus behavior.
- Structuring a page with correct landmark elements and a logical heading hierarchy (`h1` → `h2` → `h3`) so screen reader users can navigate by structure.
- Adding ARIA roles/attributes to custom components (a custom dropdown, a tab interface) that don't have a direct native HTML equivalent.

## Pros
- Gets a large amount of accessibility behavior "for free" simply by using the right element for the job.
- Improves navigability for assistive technology users via landmarks and heading structure.
- Well-documented, standardized patterns (ARIA Authoring Practices) exist for common custom widget types.

## Cons
- ARIA is easy to misuse — adding an ARIA role to an element doesn't automatically give it the keyboard/focus behavior implied by that role; you still have to implement it.
- Retrofitting semantic structure onto an existing app built with generic `<div>`s everywhere is a significant, easy-to-underestimate effort.
- "No ARIA is better than bad ARIA" — an incorrect ARIA attribute can make an experience worse for assistive technology than having none at all.

## Interview questions
1. Why does using a real `<button>` element give you accessibility behavior that a styled `<div>` with a click handler doesn't?
2. What are landmark elements, and how do screen reader users rely on them to navigate a page?
3. When should you reach for ARIA attributes, and why should native HTML always be preferred when available?
4. What's an example of ARIA being used incorrectly in a way that makes the experience worse, not better?
5. How would you audit an existing app for missing or incorrect semantic structure?
