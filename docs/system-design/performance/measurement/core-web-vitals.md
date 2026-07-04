# Core Web Vitals

## What it is
A set of standardized metrics Google defines to measure real-world user experience: **LCP** (Largest Contentful Paint — how quickly the main content loads), **INP** (Interaction to Next Paint — how responsive the page is to user input), and **CLS** (Cumulative Layout Shift — how much visible content unexpectedly moves around). They're measured from real users (field data) as well as lab tools.

## Why it's useful
- Gives a standardized, widely-adopted vocabulary for talking about "is this page fast" beyond vague impressions.
- Google uses Core Web Vitals as a search ranking signal, giving them direct business impact for SEO.
- Each metric maps to a concrete, actionable category of problem (slow content load, janky interactions, shifting layout), making them useful diagnostic starting points.

## Classic use-cases
- Setting measurable performance targets/budgets for a team to hit before shipping.
- Diagnosing why a page "feels slow" by identifying which specific vital is failing.
- Tracking real-user performance over time via tools like Google Search Console, CrUX, or RUM providers.

## Pros
- Concrete, standardized, and directly tied to business outcomes (SEO, conversion rates).
- Each metric points at a specific fixable problem rather than a vague "make it faster."
- Backed by real-user field data (CrUX), not just synthetic lab tests.

## Cons
- Optimizing narrowly for the metrics themselves (rather than genuine user experience) can lead to gaming rather than real improvement.
- Field data lags — you find out a page regressed after real users already experienced it.
- Some metrics (like CLS) can be affected by things outside a team's direct control (third-party ads/embeds).

## Interview questions
1. What does each of LCP, INP, and CLS actually measure, and what kind of problem does each point to?
2. What's the difference between lab data (Lighthouse) and field data (CrUX/real-user monitoring) for these metrics?
3. What's a common cause of poor CLS, and how would you fix it?
4. How would you set a performance budget around Core Web Vitals for a team to work against?
5. Why did Google replace First Input Delay (FID) with Interaction to Next Paint (INP)?
