# useState

## What it is
The core React hook for adding local, component-scoped state to a function component. It returns a value and a setter function; calling the setter schedules a re-render with the new value on the next render pass.

## Why it's useful
- Simplest way to give a component its own piece of mutable state without any external library.
- Triggers a re-render automatically when the value changes, keeping the UI in sync with state.
- Works for any independent, self-contained piece of state (toggles, input values, counters).

## Classic use-cases
- Controlled form inputs (tracking the current value of a text field, checkbox, etc.).
- UI toggles: modal open/closed, dropdown expanded/collapsed, active tab.
- Simple counters or flags that only one component needs to know about.

## Pros
- Minimal API — no reducers, actions, or external store needed for simple state.
- Colocated with the component that owns it, making it easy to reason about.
- No extra dependency; built into React itself.

## Cons
- State updates are asynchronous/batched, which can confuse newcomers expecting a value to update immediately after calling the setter.
- Doesn't scale well to complex state transitions with many interdependent fields — `useReducer` or a store is a better fit there.
- Storing objects/arrays requires care to avoid accidental mutation (must create a new reference to trigger a re-render).
- Lifting state up (passing it through props) becomes unwieldy once several distant components need the same state.

## Interview questions
1. Why doesn't `console.log`-ing state right after calling its setter show the updated value?
2. How does React batch multiple `setState` calls, and how did this change between React 17 and React 18?
3. When would you reach for `useReducer` instead of multiple `useState` calls?
4. What bug occurs if you mutate an array/object in state directly instead of creating a new reference, and why?
5. How does `useState`'s lazy initializer (`useState(() => expensiveInit())`) help with performance?
6. How do you decide when state should be lifted to a parent vs. kept local with `useState`?
