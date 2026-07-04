# Compound Components

## What it is
A composition pattern where several components are designed to work together as a set, sharing implicit state via context, while the parent exposes them as related sub-components (e.g., `<Select>`, `<Select.Option>`, `<Select.Trigger>`) rather than configuring everything through a single component's props.

## Why it's useful
- Lets consumers control the markup/composition of a component's internals (reordering, adding wrapper elements) without the parent needing a prop for every possible variation.
- Avoids "prop explosion" — instead of a component accepting dozens of configuration props, related pieces are just composed together as JSX children.
- Keeps shared state (e.g., "which tab is active") implicit and internally managed via context, so consumers don't have to wire it up manually.

## Classic use-cases
- Tabs (`<Tabs>`, `<Tabs.List>`, `<Tabs.Panel>`), Accordions, Select/Dropdown menus, Modals with header/body/footer sub-components.
- Any component where the consumer needs flexible control over layout/order of related pieces without an explosion of configuration props.
- Design system components that need to support many layout variations without a combinatorial explosion of props.

## Pros
- Highly flexible composition — consumers arrange sub-components however they need, within the constraints the pattern allows.
- Avoids sprawling prop APIs for components with many related pieces.
- Implicit shared state (via context) keeps the public API clean.

## Cons
- Relies on context internally, which can make sub-components unusable outside their intended parent (they'll break or no-op without the right provider).
- Harder to statically type/document than a flat prop-based API — consumers need to learn which sub-components exist and how they nest.
- Overkill for simple components that don't need this level of compositional flexibility.

## Interview questions
1. How do compound components typically share implicit state between the parent and its sub-components?
2. What's the tradeoff between a compound component API and a single component with many configuration props?
3. What happens if a sub-component (e.g., `Tabs.Panel`) is rendered outside its expected parent, and how would you guard against that?
4. When would you choose compound components over a render-prop or headless-hook based API?
5. How would you type a compound component's sub-components in TypeScript so misuse is caught at compile time?
