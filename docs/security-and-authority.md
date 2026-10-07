# Security and authority boundaries

MCP authentication and destination authorization solve different problems. A valid caller token permits tool use; it does not authorize private-network targets or arbitrary browser capabilities. The service verifies OAuth signature/issuer/audience/time/scope and separately validates URLs, resolved IP classes, redirects and browser subrequests.

Connections are mediated/pinned after validation to reduce resolver/connect mismatch. Browser native networking is unavailable as an escape path. Context/process isolation, non-root sandboxed execution and resource bounds are documented design controls; exact deployment conformance still needs candidate-specific verification.

Fetched content is untrusted external evidence. Page text cannot change tool configuration, secrets, cloud resources or request authority. JSON-LD/context URLs and links are observations rather than implicit permission to fetch further resources. Document formulas, macros and embedded code are not executed.

Operator-managed auth profiles, where authorized, are named subject/domain-bound permissions with internally resolved secrets. Caller credentials are not ordinary tool arguments. Sessions are ephemeral, credential-bearing output is redacted, and authenticated screenshots are suppressed. This review does not claim production profiles are configured.

Public explanation includes conceptual controls without exact network exclusions, operational limits, auth tenants, service accounts, secret names or review hostnames. Those configuration details remain private.

Read-oriented inspection is not a guarantee of zero remote side effects: target page scripts execute, and an explicitly authorized auth profile can perform its bounded login sequence. These capabilities do not grant arbitrary mutation authority.

The tool can inspect website evidence. It cannot establish Search Console indexed state, guarantee rich results, override robots evidence with a marketing score or mutate sites merely because a caller supplied an action-like request.
