# Keyboard Interaction

## What it is
Ensuring every interactive element and workflow on a page can be fully operated using only a keyboard — tabbing between elements in a logical order, activating controls with Enter/Space, navigating composite widgets (menus, tabs, grids) with arrow keys — without requiring a mouse at all.

## Why it's useful
- A meaningful portion of users (motor impairments, screen reader users, power users) navigate entirely via keyboard, not just as an edge case.
- Keyboard operability is often a strong proxy for overall accessibility — if something works cleanly with a keyboard, it's usually built on the right semantic foundations too.
- Catching keyboard traps (places you can tab into but never tab out of) early avoids a genuinely blocking experience for keyboard-only users.

## Classic use-cases
- Ensuring a logical, predictable tab order that matches the visual layout of the page.
- Implementing arrow-key navigation within composite widgets (tabs, menus, comboboxes, data grids) per established conventions.
- Making sure custom interactive elements respond to Enter/Space the same way native buttons/links do.

## Pros
- Directly benefits keyboard-only users and often improves the experience for everyone (predictable, learnable interaction patterns).
- Using semantic HTML elements gets much of this behavior for free, reducing custom implementation work.
- Well-established conventions (ARIA Authoring Practices) exist for how each widget type should respond to keyboard input.

## Cons
- Custom-built interactive components (that don't use native elements) require deliberately reimplementing all expected keyboard behavior.
- Keyboard traps are easy to introduce accidentally, especially with third-party widgets or custom focus-management code.
- Testing keyboard interaction thoroughly requires manually navigating the app without a mouse — easy to skip during normal development.

## Interview questions
1. What is a keyboard trap, and how would you detect one in your own application?
2. How should arrow-key navigation behave differently in a tab list vs. a menu vs. a data grid?
3. Why does using native HTML elements reduce the amount of keyboard-interaction code you need to write yourself?
4. How would you make sure a custom-built dropdown component responds correctly to keyboard input?
5. What's the relationship between tab order and the visual/DOM order of elements on the page?
