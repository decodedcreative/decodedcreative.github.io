# Slot Props

## What it is
A composition pattern where a component accepts a prop (or `children` as a function) that lets the consumer inject custom content or override rendering for a specific part of the component, while the component still controls layout, state, or behavior around it. Related to render props, but often referring specifically to named "slots" for custom content (e.g., `icon`, `header`, `footer` props that accept a node or render function).

## Why it's useful
- Lets a component stay in control of its overall structure/behavior while still giving consumers a way to customize specific pieces (an icon, a label renderer, a custom row).
- Avoids forking or wrapping a component just to change one small part of its output.
- Can expose internal state (e.g., "is this item selected") to the slot content via a render-prop function, without the consumer needing to manage that state themselves.

## Classic use-cases
- A `<Table>` component exposing a `renderRow` or `columns[].render` slot so consumers customize cell content without reimplementing the whole table.
- A `<Button>` accepting an `icon` slot prop so consumers can pass any icon without the button needing to know about every possible icon library.
- A list component exposing a slot for empty-state or loading-state content.

## Pros
- Precise, targeted customization without needing to override or wrap the entire component.
- Can pass internal state/context to the slotted content via a function-as-child/render-prop pattern.
- Keeps the component's core behavior (layout, data flow) centralized while still being flexible.

## Cons
- Can lead to a large number of slot props if a component tries to make every part customizable, undermining the simplicity it was meant to provide.
- Render-prop-style slots (`children` as a function) can be harder to read than plain JSX composition.
- Overlaps in purpose with compound components — teams need a consistent convention for when to use which.

## Interview questions
1. How does a slot prop differ from a compound component in terms of what it lets a consumer customize?
2. When would you use a render-prop-style slot (a function returning JSX) instead of a plain node prop?
3. How would a slot prop expose internal component state (e.g., "is hovered") to the customized content?
4. What's the risk of a component accumulating too many slot props over time?
5. How do slot props and compound components complement each other in a design system's component API?
