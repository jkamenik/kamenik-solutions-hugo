---
title: "Cursor Keep Alive"
date: 2025-05-13
lastmod: 2026-05-17
draft: false

keywords:
  - Cursor Keep Alive

params:
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: "No Change"

aliases:
  - /radar/techniques/cursor-keep-alive
  - /radar/techniques/cursor-keep-alive
---

A cursor keep-alive pattern lets a client poll for incremental results from a long-running server operation (for example, streaming a RAG query) without holding an open WebSocket. The server stores partial state keyed by an opaque cursor ID; each request advances or resumes delivery. This works through load balancers and WAFs that block WebSockets, at the cost of extra storage and polling latency.
