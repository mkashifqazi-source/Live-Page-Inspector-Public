# Architecture and system design

Live Page Inspector exposes exactly two tools over Streamable HTTP: inspect_live_page and inspect_live_pages. Options select bounded internal capabilities instead of adding a generic browser-control or search surface. Pydantic validates complete inputs, rejects unknown arguments and preserves a narrow tool contract.

An OAuth middleware/verifier protects the MCP route. The inspector parent controls concurrency/deadlines and launches isolated workers with bounded output and minimal runtime context. Within a worker, FAST obtains initial response evidence; RENDERED additionally captures a browser DOM under mediated networking. Evidence assembly parses initial and rendered sources separately and then applies normalization, redaction and presentation limits.

The rendered transport is unusual: Chromium's native networking is offline, while intercepted supported requests are fulfilled through the validated HTTP transport. The same destination policy, DNS/IP validation, pinned connection and redirect checks govern document and subresource fetches. Page JavaScript executes, but arbitrary caller JavaScript/shell is not a tool capability.

Mediated networking is useful but differs from an ordinary connected browser. Cookies, non-GET requests, navigation, delayed content and certain redirected resources can behave differently. Settling uses bounded capture conditions; a captured DOM is not proof of final page stability or Googlebot equivalence.

The source also contains bounded generic resource, robots/sitemap, crawl/discovery and isolated document extraction. Operator-authorized ephemeral auth profiles are a separate permission boundary and suppress authenticated screenshots. Their code is not proof of provisioned production profiles.

Cloud Run is the recorded hosting boundary: container runtime, application OAuth, runtime identity/secrets where authorized, constrained process/browser resources and revision-based validation/rollback. This showcase omits exact service identifiers, hostnames, IAM bindings and exploit-sensitive deployment configuration.
