# Provider Pattern

## What it is
A composition pattern where a component wraps part of the tree in a Context Provider to make shared state or functionality available to any descendant, without needing to pass it down explicitly through every intermediate component's props.

## Why it's useful
- Solves prop drilling for state/functionality that many descendants at varying depths need to access.
- Lets compound components and custom-hook-based APIs share implicit state cleanly (e.g., a `Tabs` provider making "active tab" available to every `Tabs.Panel`).
- Centralizes a piece of cross-cutting configuration or state (theme, auth, feature flags) at a single point in the tree.

## Classic use-cases
- Theme providers (light/dark mode, design tokens) available to every styled component in the tree.
- Compound components like `Tabs`/`Accordion`/`Select` using an internal provider to share active-state between the parent and its sub-components.
- Feature-flag or configuration providers exposing app-wide settings to any component that needs them.

## Pros
- Eliminates prop drilling for widely-needed state/functionality.
- Natural fit for compound components — the provider is often invisible to consumers, who just use the sub-components normally.
- Centralizes cross-cutting concerns (theme, auth, config) in one place.

## Cons
- Every consumer of the context re-renders when the provided value changes, which can hurt performance if not scoped carefully.
- Overuse leads to deeply nested providers ("provider hell") if every feature reaches for its own context.
- Components relying on a provider silently fail or throw if used outside their expected provider tree.

## Interview questions
1. How does the provider pattern solve prop drilling, and what's the performance tradeoff of doing so via Context?
2. How is the provider pattern used internally by compound components to share state between a parent and its sub-components?
3. What is "provider hell," and how would you avoid it in a large app with many cross-cutting concerns?
4. How would you handle (or guard against) a component being used outside its required provider?
5. How would you scope a context's re-render impact so only components that actually need the changed value re-render?
