# Retry with Backoff

## What it is
A resilience pattern where a failed request is automatically retried rather than immediately surfaced as an error, with increasing delay between each attempt (**exponential backoff** — e.g., 1s, 2s, 4s, 8s) and a small amount of randomization (**jitter**) added to that delay to avoid many clients retrying in perfect lockstep.

## Why it's useful
- Many failures (transient network blips, a momentarily overloaded server) are temporary — retrying automatically recovers from them without the user ever noticing.
- Exponential backoff avoids hammering an already-struggling server with immediate, repeated retries, which would make an ongoing problem worse.
- Jitter specifically prevents the "thundering herd" problem — if every client backs off by exactly the same schedule, they all retry at the same instant, recreating the overload they were trying to avoid.

## Classic use-cases
- Transient network errors or 5xx server responses on API calls, retried automatically a bounded number of times.
- Rate-limited endpoints (429 responses), backing off before retrying rather than immediately resubmitting.
- Any distributed system client where a downstream dependency is expected to occasionally have brief, self-resolving issues.

## Pros
- Recovers automatically from transient failures without user-visible errors or manual retry action.
- Backoff prevents retries from compounding an already-overloaded server's problems.
- Jitter specifically avoids synchronized retry storms across many clients.

## Cons
- Blindly retrying non-idempotent requests (like a payment submission) risks duplicate side effects unless paired with idempotency keys.
- Poorly bounded retry logic (no max attempts, no max delay) can mask a real, persistent failure behind a long series of retries before finally surfacing an error to the user.
- Adds complexity to error-handling logic that's easy to get subtly wrong (e.g., retrying errors that will never succeed, like a 400 Bad Request).

## Interview questions
1. Why does exponential backoff matter more than simply retrying immediately and repeatedly?
2. What problem does jitter solve that plain exponential backoff doesn't?
3. Which HTTP status codes are generally safe to retry automatically, and which aren't?
4. Why is retrying a non-idempotent request risky, and what pattern addresses that risk?
5. How would you decide the maximum number of retry attempts and the cap on backoff delay?
