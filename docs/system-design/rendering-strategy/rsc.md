# React Server Components (RSC)

## What it is
A component type that renders exclusively on the server and never ships to the client as JavaScript — its output is serialized into a special format and streamed down, where it's stitched into the page. Unlike traditional SSR (which renders HTML that then gets fully hydrated), RSC output carries no client-side JS cost at all for that component: no hydration, no bundle, no re-render on the client.

## Why it's useful
- Eliminates the JS bundle and hydration cost for any component that doesn't need interactivity — a huge share of most pages (layout, content, data display).
- Can access server-only resources directly (a database, the filesystem, private APIs) inside the component itself, without a separate API layer or client-side fetch.
- Reduces client-server request waterfalls, since data fetching happens as part of rendering on the server rather than after the client mounts and requests it.

## Classic use-cases
- Content-heavy, largely static parts of a page (article bodies, product details, dashboards) that don't need client interactivity.
- Components that fetch data directly from a database or internal service, avoiding a dedicated API endpoint just to feed the client.
- Composing a page from a mix of Server Components (for content/data) and Client Components (`"use client"`) for the interactive islands within it.

## Pros
- Zero JavaScript shipped to the client for anything that's purely a Server Component — a direct, structural win for bundle size.
- Direct backend access inside components removes a whole layer of API-building boilerplate for data that's only ever consumed by this one UI.
- Reduces waterfalls compared to client components that have to mount before they can even start fetching their own data.

## Cons
- No interactivity whatsoever — no `useState`, no effects, no event handlers; anything interactive must be an explicit Client Component.
- A genuinely new mental model (where's the client/server boundary, what crosses it) that takes real time to learn correctly.
- Ecosystem compatibility is still catching up — many libraries need updates to work correctly as Server Components, and React Context does not cross the RSC boundary.

## Interview questions
1. How does React Server Components differ from traditional SSR, given both render on the server?
2. What exactly gets sent to the client for a Server Component, if not HTML or JS?
3. How does the `"use client"` boundary work, and what determines where you'd draw it in a component tree?
4. Why can't a Server Component use `useState` or event handlers?
5. Why doesn't React Context cross the Server/Client Component boundary, and how do you work around that?
