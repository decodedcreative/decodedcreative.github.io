# Custom Hooks as Composition Primitives

## What it is
Extracting stateful logic (not UI) into a reusable custom hook (e.g., `useDisclosure`, `usePagination`, `useDebouncedValue`) that any component can call into, decoupling *behavior* from *markup* so the same logic can power completely different visual implementations.

## Why it's useful
- Separates "how this behaves" from "how this looks" — the same `useCombobox` logic could power a completely different-looking dropdown in two different products.
- Makes logic independently testable without needing to render and interact with a full component tree.
- Composes naturally — a component can combine several small hooks (`useDebouncedValue` + `useOutsideClick` + `useDisclosure`) rather than inheriting one large monolithic behavior.

## Classic use-cases
- Headless component libraries (Radix, Downshift, React Aria) that expose behavior via hooks and let consumers own all the markup/styling.
- Extracting shared logic (pagination, form state, debounced search) used across multiple differently-styled components.
- Making complex interactive behavior (drag-and-drop, keyboard navigation, focus trapping) reusable across many components.

## Pros
- Clean separation of behavior from presentation, enabling reuse across visually distinct components.
- Easier to unit test in isolation than logic embedded directly inside a component's render output.
- Composable — hooks can be combined rather than requiring rigid inheritance or wrapper hierarchies.

## Cons
- Can obscure control flow if overused — a component calling five different hooks may be hard to reason about without following each one.
- Not a natural fit for logic that's inherently tied to specific markup/DOM structure.
- Requires careful API design so hooks compose cleanly without conflicting side effects (e.g., two hooks both trying to manage focus).

## Interview questions
1. How does extracting logic into a custom hook differ from putting that logic directly inside a component?
2. What is a "headless" component library, and how do custom hooks enable that pattern?
3. How would you test a custom hook's behavior without needing to render a full component tree?
4. What risks come from composing many custom hooks together in a single component?
5. Give an example of behavior that's a good candidate for a custom hook vs. behavior that isn't.
