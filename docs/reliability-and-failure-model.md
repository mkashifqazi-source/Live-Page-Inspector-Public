# Reliability and failure taxonomy

Errors carry a stable code, normalized category, safe message, stage and retryability. Legacy fetch/browser codes map to categories such as fetch timeout, SSRF blocked, DNS blocked, redirect limit, body too large and render startup failure. Raw transport exceptions are not the public error contract.

| Boundary | Failure treatment |
|---|---|
| Invalid/unsupported arguments | Reject before dispatch; no permissive extra argument handling |
| Invalid destination or unsafe redirect | Fail closed rather than relax policy |
| Worker capacity busy | Explicit rate/capacity failure |
| Fetch/read/browser deadline | Bounded failure with stage/retry semantics |
| Resource/body/DOM/output exceeds limits | Explicit bound/omission/error semantics, depending on the contract layer |
| HTTP 404/500 captured | Return observed response evidence rather than confuse it with transport failure |
| Rendered snapshot incomplete | Preserve partial capture and warnings |
| Optional evidence missing/not requested | Keep unavailable/not-requested distinctions |
| Unsupported/malformed document | Safe extraction failure, no embedded execution |

Retryable describes a possible caller decision; it does not establish automatic retry execution. The documented core transport has no automatic retries. Batch/crawl budgets, worker lifetime and serialized output are separately bounded.

Mediated browser restrictions can explain missing content. A network-idle interval is an operational capture condition, not a universal readiness guarantee. Comparison must retain initial/rendered identity and partiality.

Release reliability is revision-specific. Historical fixture passes do not replace exact-image/container checks or authenticated no-traffic candidate validation. Existing rollback state must remain identifiable before promotion; this task changes none of it.
