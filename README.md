# Live Page Inspector

A narrowly scoped MCP evidence service that preserves HTTP, initial HTML and mediated browser-rendered observations separately.

Public Technical Overview · Private Development Repository

## Overview

LPI inspects current page/resource evidence through inspect_live_page and inspect_live_pages. FAST fetches initial response evidence; RENDERED adds a bounded browser capture and source differences. The evidence is suitable for downstream analysis without pretending it is a Google indexing verdict.

## Problem

A raw HTML fetch can miss JavaScript changes. A browser capture can obscure original headers/directives and expose unsafe networking. Useful inspection needs both evidence attribution and bounded authority.

## System Architecture

~~~mermaid
flowchart LR
  C[MCP client] --> A[OAuth / strict tool validation]
  A --> P[Parent capacity and worker bounds]
  P --> W[Isolated evidence worker]
  W --> T[Destination-validated HTTP transport]
  W --> B[Sandboxed mediated Chromium]
  B --> T
  T --> U[Allowed public resources]
  W --> E[Source attribution / redaction / output bounds]
  E --> C
~~~

## Core Components

OAuth verifier; narrow MCP server; process runner; FAST/rendered fetchers; URL/network policy; parsers; source-attributed resource/page contracts; bounded discovery/document workers; and safe output presentation.

## Key Technical Workflows

Authenticate → validate → fetch → optionally render → collect source-owned observations → compare/enrich → redact/bound → return. Explicit batches preserve individual outcomes; discovery stays bounded and requested.

## Engineering Decisions

Two tools contain scoped options. Render requests use a mediated transport while native browser networking is offline. Additive evidence contracts retain legacy projection. Availability, completeness and presentation truncation remain separate.

## Reliability / Safety / Validation

HTTP error responses can be evidence; transport failures are different. Public destination restrictions apply to redirects/subrequests. Page content is untrusted. Mediated capture differs from ordinary browsing and never claims Googlebot equivalence.

## Technology Stack

Python, MCP SDK, Starlette/Uvicorn, Pydantic, Scrapling, curl-cffi, Playwright/Chromium, lxml, DNS resolution, JWT verification, pytest/ruff and container/Cloud Run tooling. Document extraction dependencies support bounded private-source capabilities.

## Testing

Deterministic fixtures, adversarial network/document tests, OAuth/MCP cycles, legacy compatibility and serialization-budget checks, plus container/release gates. Source-recorded historical passes are not fresh tests from this task.

## Current Status

Active development. Records show production v1.0, blocked v1.1 release and newer additive contracts under development; latest diagnostics await review. Native transcript acquisition is outside LPI release scope. No live status/deployment changes were made.

## Technical Documentation

- [architecture](docs/architecture.md)
- [data model](docs/data-model.md)
- [workflows](docs/workflows.md)
- [testing and validation](docs/testing-and-validation.md)
- [reliability and failure model](docs/reliability-and-failure-model.md)
- [security and authority](docs/security-and-authority.md)
- [technical decisions](docs/technical-decisions.md)
- [project status](docs/project-status.md)
- [request lifecycle](diagrams/request-lifecycle.md)

## Repository Notice

This repository contains the public technical documentation for the project. The production source code and internal development materials are maintained separately and are not published here.
