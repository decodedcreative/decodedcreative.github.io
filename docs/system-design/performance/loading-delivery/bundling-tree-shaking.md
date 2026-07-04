# Bundling & Tree Shaking

## What it is
Bundling combines many source modules into fewer files optimized for delivery over the network. Tree shaking is the complementary step where a bundler (Vite, Webpack, Rollup) statically analyzes ES module imports/exports and eliminates code that's never actually used, so it isn't shipped to the browser.

## Why it's useful
- Reduces the number of network requests compared to shipping hundreds of individual small files.
- Removes dead code (unused exports, unreachable branches) automatically, shrinking bundle size without manual pruning.
- Modern bundlers optimize further with minification, scope hoisting, and chunk splitting on top of tree shaking.

## Classic use-cases
- Any production web app build step — this isn't optional, it's the standard build pipeline.
- Importing a single function from a large utility library (e.g., one lodash function) and shipping only that function's code.
- Splitting vendor code from application code so vendor bundles can be cached longer across deploys.

## Pros
- Standard, automatic part of modern build tooling — developers get it largely for free.
- Meaningfully shrinks shipped JavaScript, directly improving load performance.
- Works well with code splitting to produce well-sized, cacheable chunks.

## Cons
- Only works reliably with ES modules (`import`/`export`); CommonJS (`require`) code often can't be tree-shaken effectively.
- Side-effectful modules (code that runs on import, like polyfills) can block tree shaking unless explicitly marked `"sideEffects": false`.
- Misconfigured bundler settings or barrel files (`index.js` re-exporting everything) can silently prevent effective tree shaking.

## Interview questions
1. How does tree shaking rely on ES module static structure, and why does CommonJS defeat it?
2. What is the `sideEffects` field in `package.json`, and how does it affect tree shaking?
3. How can "barrel" export files hurt bundle size even with tree shaking enabled?
4. What's the difference between minification and tree shaking?
5. How would you audit a production bundle to find unexpectedly large or duplicated dependencies?
