---
title: Cursor Keep Alive
date: '2025-05-13'
lastmod: '2026-07-02'
draft: false
keywords:
- Cursor Keep Alive
- cursor polling
- resumable stream cursor
params:
  aliases:
  - cursor polling
  - resumable stream cursor
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: No Change
    subcategories:
    - api
aliases:
- /radar/techniques/cursor-keep-alive
---

**Cursor keep-alive** is an HTTP API pattern for **incremental results** from long-running work (for example, a streaming **RAG** query) when you cannot rely on an open **WebSocket**. We **assess** it under **[[Technique]]** in the garden.

## Summary

**Key points:** | Topic | Notes |
|-------|--------|
| **Storage** | Hot state in Redis; durable audit log optional |
| **Idempotency** | Same cursor + offset returns same chunk |
| **Backpressure** | Client polls with `If-None-Match` or `since` offset |
| **Errors** | Surface terminal `error` on poll; do not leave cursors orphaned |
| **Security** | Opaque, unguessable IDs; no cross-tenant cursor reuse |

**Origin in our writing:** described for RAG query APIs in [RAG Pipeline](resources/blog/20250514-rag-pipeline.md) (embedding CRUD vs streaming query split).

**References**

- [RAG Pipeline (blog)](resources/blog/20250514-rag-pipeline.md)## Personal Experience

<!-- User-owned: vault-only; never published or exported. Agents read for /tech-garden update synthesis; proofread spelling/grammar only. -->

## Details

| Topic | Notes |
|-------|--------|
| **Storage** | Hot state in Redis; durable audit log optional |
| **Idempotency** | Same cursor + offset returns same chunk |
| **Backpressure** | Client polls with `If-None-Match` or `since` offset |
| **Errors** | Surface terminal `error` on poll; do not leave cursors orphaned |
| **Security** | Opaque, unguessable IDs; no cross-tenant cursor reuse |

**Origin in our writing:** described for RAG query APIs in [RAG Pipeline](resources/blog/20250514-rag-pipeline.md) (embedding CRUD vs streaming query split).

**References**

- [RAG Pipeline (blog)](resources/blog/20250514-rag-pipeline.md)
