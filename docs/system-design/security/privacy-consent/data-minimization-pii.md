# Data Minimization & PII

## What it is
The principle of only collecting, processing, and retaining the personal data (PII — personally identifiable information) that's genuinely necessary for a given purpose, and for no longer than needed. In practice, this shapes concrete engineering decisions: what gets logged, what's included in analytics events, what's stored in URLs, and how long records are kept.

## Why it's useful
- Reduces the blast radius of any future data breach or leak — data that was never collected can't be exposed.
- Makes compliance obligations (GDPR/CCPA data requests, deletion) simpler, since there's less scattered PII to track down across systems.
- Forces deliberate thinking about what data a feature actually needs, often surfacing unnecessary collection that provides little real value.

## Classic use-cases
- Avoiding putting PII (emails, names, tokens) in URL query parameters, since URLs get logged by servers, proxies, and leak via the `Referer` header.
- Scrubbing or avoiding logging PII in application logs and error tracking tools by default.
- Setting explicit retention policies (auto-delete analytics data after N months) rather than keeping everything indefinitely by default.

## Pros
- Directly reduces both privacy risk and the scope/cost of compliance obligations.
- Encourages a healthier default engineering posture — "do we actually need this data" becomes a normal question to ask.
- Smaller, more deliberate datasets are often easier to reason about and secure than large, sprawling ones collected "just in case."

## Cons
- Can conflict with product/analytics teams wanting more data for personalization or measurement — requires deliberate tradeoff conversations.
- Retrofitting minimization onto systems that already over-collect (existing logs, analytics schemas) is nontrivial cleanup work.
- Requires ongoing discipline across a whole team/organization, not a single one-time technical fix.

## Interview questions
1. Why is putting PII in a URL query parameter specifically risky, given how URLs get logged and shared?
2. How would you audit an existing application's logging/analytics pipeline for unintentional PII collection?
3. What's the tradeoff between data minimization and a product team's desire for richer analytics/personalization data?
4. How would you design a retention policy for user data, and what factors would influence how long is "long enough"?
5. How does data minimization make responding to a GDPR/CCPA data request easier in practice?
