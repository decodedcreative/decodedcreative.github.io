# useRef

## What it is
A React hook that returns a mutable object (`{ current: value }`) which persists for the lifetime of the component but does **not** trigger a re-render when its value changes. It's commonly used to hold references to DOM nodes or to store values that need to survive re-renders without participating in the render cycle.

## Why it's useful
- Lets you store a mutable value across renders without causing extra re-renders, unlike `useState`.
- Provides direct access to DOM elements (e.g., to call `.focus()`, measure size, or integrate a non-React library).
- Useful for holding "instance variables" in function components — things like timers, previous values, or mutable flags.

## Classic use-cases
- Managing focus, text selection, or media playback on a DOM element.
- Storing a `setTimeout`/`setInterval` ID so it can be cleared later.
- Tracking a previous prop/state value to compare against the current one (e.g., detecting a change).
- Integrating third-party non-React libraries that need a direct DOM node reference.

## Pros
- Mutating `.current` doesn't cause a re-render, which is exactly right for values that shouldn't affect the UI directly.
- Persists across renders without being reset, unlike a plain local variable inside the component function.
- Simple, direct way to access underlying DOM nodes when React's declarative model isn't enough (measurements, imperative APIs).

## Cons
- Reading/writing `ref.current` during render (rather than in effects/handlers) breaks React's rendering model and can cause bugs.
- Because updates don't trigger re-renders, it's easy to misuse `useRef` for state that should actually be `useState` — leading to a UI that's out of sync with the underlying value.
- Overuse for values that actually affect rendering leads to subtle bugs where the UI doesn't update as expected.

## Interview questions
1. Why doesn't updating `ref.current` cause a component to re-render, and when is that the right behavior?
2. When would you use `useRef` instead of `useState`, and what goes wrong if you pick the wrong one?
3. How do you use `useRef` to access and imperatively manipulate a DOM node?
4. How would you use `useRef` to store the previous value of a prop or state variable for comparison?
5. What's the danger of reading or writing a ref's value during the render phase itself?
6. How does `forwardRef` relate to `useRef`, and when do you need it?
