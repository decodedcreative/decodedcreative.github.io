# Error Tracking

## What it is
A service (Sentry, Bugsnag, Rollbar) that automatically captures unhandled exceptions and errors from a running frontend application in production, aggregating them with stack traces, user/session context, and frequency data so developers know what's actually breaking for real users.

## Why it's useful
- Surfaces production errors that would otherwise be invisible — most users don't file a bug report when something breaks, they just leave.
- Aggregates duplicate errors across many users into a single trackable issue, with counts showing real-world impact/severity.
- Captures rich context (browser, OS, user, breadcrumbs of recent actions) that makes reproducing and fixing bugs far faster than a vague user report.

## Classic use-cases
- Catching unhandled exceptions in production that weren't caught by tests or manual QA.
- Prioritizing bug fixes by real-world frequency/impact rather than guesswork.
- Correlating a spike in errors with a specific deploy (release tracking) to catch regressions fast.

## Pros
- Gives visibility into production failures that are otherwise completely invisible to the team.
- Rich context (breadcrumbs, session replay in some tools) dramatically speeds up debugging.
- Release tracking makes it fast to correlate error spikes with a specific deploy and roll back if needed.

## Cons
- Can generate noisy, low-value errors (browser extension conflicts, ad-blocker interference) that need filtering/triage.
- Capturing detailed context (session replay, user data) raises privacy considerations that need to be handled carefully.
- Doesn't catch everything — silent failures that don't throw (e.g., a feature quietly not working) won't show up without additional instrumentation.

## Interview questions
1. How does an error tracking tool capture and deduplicate errors across many different users into one issue?
2. What is release tracking, and how does it help you correlate a bug with a specific deploy?
3. How would you filter out noisy, low-value errors (e.g., from browser extensions) without missing real issues?
4. What privacy considerations come into play when capturing detailed error context or session replays?
5. What kinds of bugs does error tracking fundamentally miss, and how would you catch those instead?
