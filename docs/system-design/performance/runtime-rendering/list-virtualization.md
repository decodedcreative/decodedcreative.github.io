# List Virtualization

## What it is
A rendering technique for long lists/grids where only the items currently visible in the viewport (plus a small buffer) are actually mounted in the DOM. As the user scrolls, off-screen items are unmounted/recycled and new ones are rendered in, regardless of how many total items exist. Common libraries: `react-window`, `react-virtualized`, `TanStack Virtual`.

## Why it's useful
- Rendering thousands of DOM nodes at once is slow and memory-heavy; virtualization keeps the DOM node count roughly constant regardless of list size.
- Keeps scroll performance smooth even for lists with tens of thousands of rows.
- Avoids the browser doing layout/paint work for elements the user can't even see.

## Classic use-cases
- Large data tables or grids (spreadsheets, admin panels with thousands of rows).
- Chat/message feeds with long scrollback history.
- Infinite-scroll feeds (social media, search results) where the underlying dataset keeps growing.

## Pros
- Dramatically improves scroll performance and memory usage for large lists.
- Decouples rendering cost from total item count — 100,000 items cost roughly the same as 100 visible ones.
- Mature libraries handle the tricky math (scroll position, item recycling, variable heights) for you.

## Cons
- Breaks native browser behaviors that assume all items are in the DOM: `Ctrl+F` find-in-page, screen reader navigation, and SEO indexing of list content.
- Variable-height items are significantly harder to virtualize correctly than fixed-height ones.
- Adds implementation complexity (measuring, scroll-position math) compared to a plain `.map()` render.

## Interview questions
1. Why does rendering a very long list without virtualization cause performance problems, specifically?
2. How does a virtualization library decide which items to render at a given scroll position?
3. What accessibility tradeoffs does virtualization introduce, and how would you mitigate them?
4. How do you handle virtualizing a list where item heights vary and aren't known in advance?
5. How would you combine virtualization with infinite scrolling/pagination from a server-state library?
