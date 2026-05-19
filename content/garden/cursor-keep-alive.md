---
title: "Cursor Keep Alive"
date: 2025-05-13
lastmod: 2026-05-18
draft: false

keywords:
  - Cursor Keep Alive
  - cursor polling
  - resumable stream cursor

params:
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: "No Change"
    subcategories:
      - api

aliases:
  - /radar/techniques/cursor-keep-alive
---

**Cursor keep-alive** is an HTTP API pattern for **incremental results** from long-running work (for example, a streaming **RAG** query) when you cannot rely on an open **WebSocket**. The name refers to an **opaque cursor ID**, not the **[[Cursor]]** IDE or **[[cursor-agent]]**. We rate it **assess**: reach for it when load balancers or WAFs block WebSockets; prefer simpler streaming when the network allows.

## Blurb

> The server stores partial state keyed by an opaque cursor ID; each request advances or resumes delivery. This works through load balancers and WAFs that block WebSockets, at the cost of extra storage and polling latency.

## Summary

**Problem:** clients want token-by-token or chunk-by-chunk output from slow server work (LLM generation, retrieval, batch transforms) without holding a long-lived connection.

**Pattern:**

1. **Start** (`POST`): enqueue work; return `cursor_id` (and optional first chunk).
2. **Poll** (`GET /…/cursor/{id}`): return the next chunk, cursor position, and `done` / `error` status.
3. **Store** server-side state (Redis, DynamoDB, SQL) with **TTL** and idempotent reads.

**Compared to other streaming options:**

| Approach | Pros | Cons |
|----------|------|------|
| **WebSocket** | Low latency, true push | Often blocked or sticky-session heavy behind WAF/LB |
| **SSE** (Server-Sent Events) | Simple HTTP, one-way push | Still long-lived; some proxies time out |
| **Cursor keep-alive** | Plain request/response; survives strict proxies | Polling latency; you operate cursor storage |
| **Buffer then respond** | Simplest server | Poor UX for LLM-length waits |

**When to assess:** **[[REST]]**/**[[OpenAPI]]** query APIs behind corporate ingress, **[[Kubernetes]]** Ingress + WAF, or serverless with hard request timeouts (start async job + poll from the client).

**When to skip:** you control the edge and WebSockets or SSE are allowed; or latency under ~200 ms matters and polling is too coarse.

**Implementation notes:** authenticate cursor IDs; bind cursors to user/session; cap concurrent cursors; garbage-collect on TTL; return `410`/`404` when expired. Document the contract in **[[OpenAPI]]** (start + poll operations).

## Details

| Topic | Notes |
|-------|--------|
| **Storage** | Hot state in Redis; durable audit log optional |
| **Idempotency** | Same cursor + offset returns same chunk |
| **Backpressure** | Client polls with `If-None-Match` or `since` offset |
| **Errors** | Surface terminal `error` on poll; do not leave cursors orphaned |
| **Security** | Opaque, unguessable IDs; no cross-tenant cursor reuse |

**Origin in our writing:** described for RAG query APIs in [RAG Pipeline](resources/blog/20250514-rag-pipeline.md) (embedding CRUD vs streaming query split).

**Garden pattern:** **assess** for constrained HTTP edges; **adopt** straightforward streaming (WebSocket/SSE) when infrastructure permits.

**References**

- [RAG Pipeline (blog)](resources/blog/20250514-rag-pipeline.md)
