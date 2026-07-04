# Controlled Vs Uncontrolled

## What it is
Two approaches to where a component's state lives: a **controlled** component receives its value and change handler as props, with the parent owning the state entirely; an **uncontrolled** component manages its own internal state, optionally exposing a way to read or influence it (e.g., a `defaultValue` or a ref).

## Why it's useful
- Controlled components give the parent full ownership and visibility over state, enabling validation, syncing multiple inputs, or driving the UI from external state (e.g., Redux, form libraries).
- Uncontrolled components reduce boilerplate and re-renders for simple cases where the parent doesn't need to react to every change.
- Many reusable components support both modes, letting consumers choose the right level of control for their use case.

## Classic use-cases
- Form inputs: controlled for real-time validation/synced state, uncontrolled for simple forms handled only on submit (common with libraries like React Hook Form, which favor uncontrolled inputs for performance).
- A custom `Accordion` or `Tabs` component supporting both a controlled `activeIndex`/`onChange` pair and an uncontrolled `defaultActiveIndex` for simpler use.
- Any reusable component where some consumers need to drive/observe state externally while others just want default behavior.

## Pros
- Controlled: full parent visibility/control, easy to keep in sync with external state or validation logic.
- Uncontrolled: less boilerplate, fewer re-renders, simpler for straightforward use cases.
- Supporting both in a component's API maximizes flexibility for different consumers.

## Cons
- Controlled components require the parent to correctly manage state and re-render on every change, which can hurt performance if overused for high-frequency updates (e.g., every keystroke).
- Uncontrolled components are harder to synchronize with other state or validate in real time.
- Supporting both modes in one component's API adds implementation complexity (handling the "is this controlled or not" branching correctly).

## Interview questions
1. How do you implement a component that supports being either controlled or uncontrolled depending on which props are passed?
2. Why do libraries like React Hook Form favor uncontrolled inputs by default, and what problem does that solve?
3. What bugs can occur if a component "switches" between controlled and uncontrolled during its lifetime (e.g., a value prop going from `undefined` to a real value)?
4. When would you force a component to be fully controlled rather than supporting both modes?
5. How does the controlled/uncontrolled choice affect a component's re-render frequency?
