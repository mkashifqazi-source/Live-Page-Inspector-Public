# Technical decisions

## Two tools with bounded internal capabilities

**Context:** Evidence collection can expand into generic automation.

**Decision:** Keep single and batch inspection as the public MCP surface; profiles/options select scoped behavior.

**Why:** The governing contract preserves a narrow read-oriented interface.

**Alternatives considered:** Generic search and unrestricted browser control are explicitly excluded.

**Consequences:** Input/schema discipline matters; additional evidence types must fit the bounded contract.

**Current status:** Implemented public tool catalog.

## Mediate browser networking

**Context:** Rendering requires page scripts/subresources while destinations remain untrusted.

**Decision:** Fulfill intercepted supported requests through the same validated transport with native browser networking offline.

**Why:** Extend destination validation to render-time networking.

**Alternatives considered:** Unrestricted native connectivity is excluded by the recorded security architecture; no blanket browser-equivalence claim is made.

**Consequences:** Safer authority boundary, but cookies/non-GET/navigation/delayed resource behavior can differ from normal browsing.

**Current status:** Implemented and fixture-tested in source records; deployment gates remain version-specific.

## Add contracts without silently replacing legacy output

**Context:** Richer source-attributed evidence needs new availability and completeness semantics.

**Decision:** Attach independently versioned optional contracts and retain a legacy projection.

**Why:** Improve evidence semantics while permitting compatibility verification.

**Alternatives considered:** No exhaustive historical comparison was located; source records explicitly require unchanged legacy behavior.

**Consequences:** Extra assembly/redaction/budget tests and clear implementation-versus-deployment status.

**Current status:** Additive development present; latest diagnostics candidate pending review.
