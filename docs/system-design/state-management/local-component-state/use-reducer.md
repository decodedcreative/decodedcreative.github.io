# useReducer

## What it is
A React hook for managing local component state via a reducer function — a pure function `(state, action) => newState` — similar in spirit to Redux but scoped to a single component (or shared via Context). You dispatch actions instead of calling a setter directly, and the reducer computes the next state.

## Why it's useful
- Centralizes all state-transition logic in one function, making complex state changes easier to follow and test.
- Makes state transitions explicit and named (actions), instead of scattered `setX(...)` calls throughout a component.
- Scales better than several independent `useState` calls when many pieces of state change together in response to the same events.

## Classic use-cases
- Forms with many interdependent fields, validation states, and submission states.
- Complex UI widgets (multi-step wizards, drag-and-drop editors) where a single action can affect several state fields at once.
- Components where the next state depends on the previous state in non-trivial ways.

## Pros
- Keeps related state-transition logic in one testable, pure function.
- Named actions make it easier to trace what caused a state change (especially with devtools/logging).
- Avoids the "prop drilling of setters" problem — dispatch is a single stable function to pass down.
- Can be combined with Context to share both state and dispatch across a subtree without a full state-management library.

## Cons
- More boilerplate than `useState` for genuinely simple state (a single toggle doesn't need a reducer).
- Still local to a component/subtree — doesn't replace global state management for app-wide concerns.
- Reducer logic can grow large and become its own maintenance burden if not split up.
- Less familiar to developers who haven't used Redux-style patterns before.

## Interview questions
1. When would you choose `useReducer` over several `useState` calls in the same component?
2. How does `useReducer` compare conceptually to Redux, and where do the similarities end?
3. How would you share state and dispatch from `useReducer` across a subtree using Context?
4. What makes a reducer function "pure," and why does that matter for predictability and testing?
5. How would you handle asynchronous logic (API calls) in a component that uses `useReducer`?
6. How do you test a reducer function in isolation from the component that uses it?
