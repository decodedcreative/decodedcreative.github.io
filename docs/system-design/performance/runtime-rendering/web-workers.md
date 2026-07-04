# Web Workers

## What it is
A browser API for running JavaScript on a separate background thread, distinct from the main thread that handles the DOM, rendering, and user interaction. Workers communicate with the main thread via message passing (`postMessage`) rather than shared memory, and cannot directly touch the DOM.

## Why it's useful
- Moves genuinely expensive computation off the main thread, so it doesn't block rendering, scrolling, or input handling.
- Lets CPU-heavy work (parsing, image processing, complex calculations) run in parallel with the UI staying responsive.
- Isolates crashes/infinite loops in the worker's code from freezing the entire page.

## Classic use-cases
- Parsing or transforming large datasets (CSV/JSON) client-side without freezing the UI.
- Client-side image/video processing or compression.
- Running expensive algorithms (search indexing, cryptography, complex validation) triggered by user interaction.

## Pros
- Directly solves main-thread jank caused by CPU-bound work, which memoization/virtualization can't fix.
- True parallelism (multiple cores) rather than just better scheduling of work on one thread.
- Well-supported browser API with no framework dependency required.

## Cons
- No direct DOM access — all UI updates still have to happen on the main thread via message passing, adding architectural complexity.
- Passing large amounts of data to/from a worker has serialization overhead unless using transferable objects/`SharedArrayBuffer`.
- Overkill for anything that isn't genuinely CPU-bound; most UI jank is caused by rendering cost, not raw computation, so workers don't help there.

## Interview questions
1. What kind of performance problems do Web Workers solve that memoization or virtualization can't?
2. How do the main thread and a worker communicate, given they don't share memory directly?
3. What are transferable objects, and why do they matter for passing large data to a worker efficiently?
4. Why can't a Web Worker manipulate the DOM directly?
5. How would you decide whether a given expensive operation belongs in a Web Worker vs. just optimizing the algorithm itself?
