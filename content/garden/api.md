---
title: "API"
date: 2025-12-29
lastmod: 2026-05-18
draft: false

keywords:
  - API

params:
  garden:
    kind: subcategory
    parent_category: technique
    subcategory_slug: api

aliases:
---

Under [[Technique]], **API** covers how systems expose and consume programmatic interfaces, contracts for moving data and invoking behavior across process and network boundaries.

**In this subcategory:** style and protocol choices for service interfaces, [[REST]] (default for HTTP APIs), [[gRPC]] (RPC/protobuf where it fits), [[GraphQL]] (query layer; **hold** for new greenfield work in our garden). **Related:** [[OpenAPI]] for describing and documenting HTTP APIs; [[RPC]] as the broader pattern gRPC builds on.

**Garden stance:** **adopt** [[REST]] with [[OpenAPI]] specs for most HTTP services. **assess** [[gRPC]] for internal high-performance or tooling-shaped RPC (e.g. provider plugins). **hold** [[GraphQL]] unless you have a concrete hyper-scale or client-heterogeneity problem it solves better than REST + OpenAPI.

Tag an item here when the note is about an API *style or protocol*, not a specific product SDK or agent tool surface.
