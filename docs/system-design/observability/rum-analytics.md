# RUM & Analytics

## What it is
Real User Monitoring (RUM) collects performance and behavioral data directly from real users' browsers in production (as opposed to synthetic/lab testing), covering metrics like Core Web Vitals, page load times, and interaction patterns. Analytics tools layer on top to track user behavior — page views, feature usage, conversion funnels.

## Why it's useful
- Measures what real users on real devices/networks actually experience, which often differs significantly from a fast dev machine or synthetic Lighthouse run.
- Segments performance/behavior data by geography, device, connection type, and browser, revealing problems that only affect specific user segments.
- Connects technical metrics (load time) to business metrics (conversion rate), making the business case for performance work concrete.

## Classic use-cases
- Tracking real-world Core Web Vitals distribution across all users, not just a single lab measurement.
- Identifying that a specific user segment (e.g., mobile users on slow networks) has significantly worse experience than the aggregate average suggests.
- Funnel analysis — where users drop off in a multi-step flow (checkout, onboarding).

## Pros
- Reflects genuine real-world conditions rather than idealized lab/synthetic testing.
- Enables segmentation that reveals problems hidden by aggregate averages.
- Directly ties technical performance metrics to business outcomes (conversion, retention).

## Cons
- Requires real traffic to be meaningful — low-traffic pages/features won't have statistically useful RUM data.
- Collecting detailed behavioral data raises privacy/consent considerations (cookie banners, data retention policies).
- Can be noisy — outliers (a user on a train tunnel losing connection) need to be filtered from meaningful trend analysis.

## Interview questions
1. What's the difference between RUM and synthetic/lab performance testing (e.g., Lighthouse), and why do you need both?
2. How would you use RUM data segmented by device/network to find a problem hidden by an aggregate average?
3. How do you connect a performance metric (e.g., LCP) to a business metric (e.g., conversion rate) using this data?
4. What privacy/consent considerations apply to collecting RUM and analytics data from real users?
5. How would you filter out noisy outliers without losing genuinely meaningful trend signals?
