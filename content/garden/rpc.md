---
title: Remote Procedure Call (RPC)
date: '2025-12-21'
lastmod: '2026-07-01'
draft: false
keywords:
- Remote Procedure Call (RPC)
- Remote Procedure Call
params:
  aliases:
  - Remote Procedure Call
  garden:
    kind: item
    usefulness: hold
    category: technique
    movement: No Change
    subcategories:
    - api
---

[Remote procedure call (RPC)](https://en.wikipedia.org/wiki/Remote_procedure_call) exposes local function calls across process or network boundaries. We **hold** it as the default integration style for distributed systems. RPC began as **[[IPC]]** over the network stack, which is reasonable on one host. Once peers live on different machines, the call metaphor fights versioning, failure modes, and team boundaries.

## Blurb

> In distributed computing, a remote procedure call is when a computer program causes a procedure to execute in a different address space as if it were a local procedure call, without the programmer explicitly writing details for the remote interaction.

## Summary

**Why hold:** RPC hides latency, partial failure, and contract evolution behind a synchronous function shape. Teams inherit tight coupling, brittle client stubs, and debugging pain when services move or scale independently. Prefer resource-oriented **[[REST]]** with **[[OpenAPI]]** for most HTTP services.

**When RPC anyway:** local **[[IPC]]**-shaped control planes, plugin hosts, or tooling protocols where both sides share a lifecycle (for example a CLI talking to a co-located daemon). **[[gRPC]]** is **assess** in those bounded cases, not a greenfield default for product APIs.

**Relationship to [[IPC]]:** same-machine RPC is often just IPC with a serializer. Treat cross-host RPC as a service boundary design problem, not a convenience wrapper.

## Details

| Topic | Notes |
|-------|--------|
| **Default alternative** | **[[REST]]** + explicit DTOs and error models |
| **High-performance internal** | **assess** **[[gRPC]]** with strict schema and ownership |
| **Local tooling** | **[[IPC]]** primitives or local **[[gRPC]]** before remote RPC |
| **Failure handling** | Timeouts, retries, and idempotency must be designed; RPC stubs do not provide them |
| **Garden link** | **[[API]]** subcategory stance: adopt REST, assess gRPC, hold RPC as default |
