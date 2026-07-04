# Storybook

## What it is
A tool for developing, documenting, and visually testing UI components in isolation from a full application — each component is rendered in its own "story" with a given set of props/states, browsable in a standalone UI outside the app it belongs to.

## Why it's useful
- Lets you build and test a component without needing to run the full application or navigate to the specific screen that uses it.
- Documents every component's variants/states (loading, error, empty, disabled) in one browsable place, serving as living documentation for both design and engineering.
- Integrates with visual regression testing (e.g., Chromatic) and accessibility tooling, catching issues per-component rather than only within full pages.

## Classic use-cases
- Developing a new component in isolation before it's wired into a real feature/page.
- Giving designers and QA a way to review every component state without needing to reproduce it inside the live app.
- Serving as the foundation for visual regression testing across an entire component library.

## Pros
- Dramatically speeds up component development by removing the need to navigate a full app to reach a given state.
- Acts as living, always-up-to-date documentation, since stories are just code alongside the components.
- Strong ecosystem of add-ons: accessibility checks, visual regression, interaction testing, design tool integration.

## Cons
- Writing and maintaining stories is extra work on top of the component itself, and can go stale if not kept up to date.
- Components that are tightly coupled to app-level context (routing, global state) can be awkward to render in isolation without extra setup.
- Another tool/build step to maintain in the project's toolchain.

## Interview questions
1. What problem does developing a component in Storybook solve compared to building it directly inside the app?
2. How would you handle a component that depends on app-level context (e.g., a router or global state provider) inside Storybook?
3. How does Storybook serve as living documentation, and what keeps it from going stale?
4. How does Storybook integrate with visual regression testing tools like Chromatic?
5. What's the tradeoff of maintaining stories for every component vs. only the most reused/critical ones?
