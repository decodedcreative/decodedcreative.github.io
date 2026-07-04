# Redux Toolkit

## What it is
The official, opinionated toolset for writing Redux logic, designed to eliminate the boilerplate of "classic" Redux (hand-written action types, action creators, and switch-statement reducers). It bundles `configureStore`, `createSlice`, `createAsyncThunk`, and sensible defaults (Immer for immutable updates, Redux DevTools, Thunk middleware) out of the box.

## Why it's useful
- Cuts the boilerplate that made classic Redux tedious — one `createSlice` call replaces action types, action creators, and a reducer.
- Uses Immer under the hood, so reducers can be written with "mutating" syntax while staying immutable.
- Provides a single, predictable global store with time-travel debugging via Redux DevTools.

## Classic use-cases
- Large applications with complex, deeply shared client state that many features read and write.
- Apps needing predictable, testable state transitions with strict unidirectional data flow.
- Teams that want a single, centralized store as the source of truth, often paired with RTK Query for server state.

## Pros
- Mature, battle-tested pattern with a huge ecosystem, middleware, and community knowledge.
- Excellent devtools: time-travel debugging, action logging, state diffing.
- Enforced unidirectional data flow makes state changes traceable and testable.
- `createSlice`/Immer significantly reduce the boilerplate that plagued classic Redux.

## Cons
- Still more ceremony (store, slices, dispatch, selectors) than lighter alternatives like Zustand.
- A single global store can encourage putting things in Redux that would be better as local component state.
- Learning curve for newcomers unfamiliar with the action/reducer/selector mental model.
- Overkill for small apps or state that's only shared between a couple of components.

## Interview questions
1. What problems does Redux Toolkit solve compared to "classic" hand-written Redux?
2. How does Immer let you write "mutating" reducer code while preserving immutability?
3. Walk through the data flow: dispatch → reducer → store → selector → re-render.
4. How would you decide what should live in Redux vs. local component state vs. server-state cache?
5. What is `createAsyncThunk`, and what problem does it solve for async logic in Redux?
6. How does Redux DevTools' time-travel debugging work under the hood?
7. Compare Redux Toolkit to Zustand and React Context — when is each the right choice?
