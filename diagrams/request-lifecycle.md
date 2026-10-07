# Request and evidence lifecycle

~~~mermaid
sequenceDiagram
  participant C as MCP client
  participant A as Auth + input
  participant P as Parent
  participant W as Worker
  participant T as HTTP transport
  participant B as Browser
  C->>A: Inspect
  A->>P: Authorize and validate
  P->>W: Bounded dispatch
  W->>T: Fetch / revalidate
  T-->>W: Initial response
  opt Rendered mode
    W->>B: Isolated render
    B->>T: Supported subrequests
    T-->>B: Validated responses
    B-->>W: DOM / capture state
  end
  W-->>P: Bounded evidence or error
  P-->>C: Redacted result
~~~

This is a logical lifecycle, with cleanup at worker/context boundaries. It does not expose actual deployment topology or credentials.
