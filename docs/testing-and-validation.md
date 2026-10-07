# Testing and validation

The real verification strategy uses deterministic fixture servers and generated auth keys, parser/unit regressions, security/adversarial tests, in-process MCP client cycles, Windows/Linux/container gates, installed-package checks, output-budget/compatibility oracles and limited optional external smoke checks.

Fixtures cover status/redirects, metadata/directives, schema, links, rendered scripts/subresources, settling, resource/document types and extraction limits. OAuth tests cover signature, issuer, audience, expiry and scope. Network tests exercise blocked destinations, redirect/subrequest validation and escape prevention. Document tests include hostile archives and parser bounds.

Additive contract tests compare preserved legacy outputs and prior accepted contract sections rather than treating a new implementation as its own oracle. Near-cap worker/parent cases validate actual serialized-byte envelopes, redaction and omission semantics. Complete/partial/indeterminate states are tested separately from presentation truncation.

Source records report historical acceptance runs. The inspected current status records newer diagnostics as pending independent review, with focused validations and Linux infrastructure unavailable. The recorded v1.1 release remains blocked, with exact fresh-image/authenticated candidate gates outstanding in its release record.

No tests, browsers, cloud calls or deployments were run during the showcase task. Historical source counts are intentionally not repeated as a fresh certification. Current candidate acceptance requires its own review and environment-specific checks.
