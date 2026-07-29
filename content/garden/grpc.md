---
title: gRPC
date: '2025-12-21'
lastmod: '2026-07-29'
draft: false
keywords:
- gRPC
params:
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: No Change
    subcategories:
    - api
---

[gRPC](https://grpc.io/). A high-performance, open source universal RPC framework We **assess** it under **[[Technique]]** in the garden.

## Summary

**Key points:**

| Topic | Notes |
|-------|--------|
| **Transport** | HTTP/2; binary **[[Protobuf]]** payloads |
| **Strengths** | Streaming, strong contracts, efficient internal calls |
| **Risks** | **[[RPC]]** impedance across teams; debugging and versioning tax |
| **Local / IPC** | **[[Docker]]**, **[[Terraform]]**, and similar tools use gRPC-shaped local APIs |
| **Alternatives** | **[[REST]]** (default), **[[GraphQL]]** (**hold** for new greenfield) |## Personal Experience

<!-- User-owned: vault-only; never published or exported. Agents read for /tech-garden update synthesis; proofread spelling/grammar only. -->

## Details

| Topic | Notes |
|-------|--------|
| **Transport** | HTTP/2; binary **[[Protobuf]]** payloads |
| **Strengths** | Streaming, strong contracts, efficient internal calls |
| **Risks** | **[[RPC]]** impedance across teams; debugging and versioning tax |
| **Local / IPC** | **[[Docker]]**, **[[Terraform]]**, and similar tools use gRPC-shaped local APIs |
| **Alternatives** | **[[REST]]** (default), **[[GraphQL]]** (**hold** for new greenfield) |
