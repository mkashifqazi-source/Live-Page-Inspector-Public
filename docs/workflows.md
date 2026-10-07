# Inspection workflows

## Single FAST inspection

Verify caller → validate input/options → acquire bounded worker capacity → validate destination → fetch with redirect revalidation → record HTTP evidence → parse applicable resource/initial HTML → assemble source-attributed result → redact/bound presentation → return.

HTTP error status can itself be useful evidence. An observed 404 is different from a transport failure that never captured a response.

## RENDERED inspection

Perform controlled initial retrieval → create isolated browser context → mediate supported subresource requests through the same destination policy → execute page scripts → wait within settling/deadline bounds → capture DOM/visible text/completion metadata → compare initial and rendered evidence → destroy context/processes.

Visual/declarative options can select rendered behavior. Caller-supplied code, arbitrary headers/cookies/proxies and unrestricted automation are outside the tool contract. Any operator auth profile has subject/domain authorization, internal credential references, redaction and ephemeral lifecycle controls.

## Batch and discovery

Explicit URL batches retain input order and return indexed success/error evidence for each input under total bounds. Crawl/discovery is explicit, bounded and policy-controlled; normal inspection does not silently recurse through every link/sitemap. Duplicate and redirect identity handling is separate from proof of complete site coverage.

## Document/resource inspection

MIME/resource classification dispatches bounded text/JSON/XML/robots/sitemap or document extraction. Document workers treat formulas/macros/embedded resources as evidence or rejected content, not executable authority. Unsupported or partial extraction stays explicit.

## New contract enrichment

Captured snapshots feed additive analysis, redaction and serialization budgets. Presentation omission is distinct from incomplete capture or analysis. Later diagnostics cannot turn a partially settled DOM into complete page evidence.
