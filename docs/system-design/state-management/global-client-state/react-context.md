# React Context

## What it is
A built-in React feature for passing data through the component tree without manually threading props down through every intermediate component ("prop drilling"). A `Provider` supplies a value, and any descendant component can read it via `useContext`.

## Why it's useful
- Solves prop drilling for values needed by many components at different nesting depths.
- Built into React — no extra dependency or library to learn.
- Well suited for state that changes infrequently (theme, locale, authenticated user).

## Classic use-cases
- Theme (light/dark mode) or locale/i18n settings shared across the whole app.
- Authenticated user/session info that many components need to read.
- Dependency injection for things like a configured API client or feature-flag service.

## Pros
- No extra library required — part of core React.
- Simple mental model: `createContext`, `Provider`, `useContext`.
- Great for rarely-changing, broadly-needed values.

## Cons
- Every consumer re-renders whenever the context value changes, with no built-in selective subscription — this gets expensive for frequently-changing state.
- Not designed as a full state-management solution (no built-in devtools, middleware, or action patterns).
- Combining multiple contexts for different concerns can lead to deeply nested providers ("provider hell").
- Doesn't handle async/server state — still need a separate tool for API data caching.

## Interview questions
1. Why does every consumer of a context re-render when its value changes, and how would you mitigate that?
2. When would you reach for Context vs. Zustand/Redux for shared state?
3. How would you split a context to avoid unnecessary re-renders (e.g., separate state and dispatch contexts)?
4. What is "provider hell," and how do you avoid it in a large app with many contexts?
5. How does `useContext` interact with React's reconciliation — does it cause the whole subtree to re-render or just the consumers?
6. How would you memoize a context value to avoid re-renders caused by a new object reference on every parent render?
