---
title: SpiceDB
date: '2023-07-23'
lastmod: '2026-07-01'
draft: false
keywords:
- SpiceDB
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: New
---

[SpiceDB](https://authzed.com/spicedb/) is an open-source, Google [[Zanzibar]]-inspired database for fine-grained authorization. It stores relationship tuples, evaluates permission checks over a graph, and stays separate from authentication. We **assess** it as the leading open ReBAC engine when apps need global-scale authorization beyond **[[RBAC]]** or **[[Open Policy Agent]]** policy checks.

## Blurb

> SpiceDB is an open-source, Google Zanzibar-inspired database system for real-time, security-critical application permissions.

## Summary

**What it is:** Authorization datastore and API from AuthZed. Developers define a SpiceDB schema, write relationships from app code, and call Check, Lookup, and Expand APIs.

**When to use:** Product needs relationship-based access control modeled after **[[Zanzibar]]**. You want schema validation, ZedTokens for consistency, and a mature OSS core with optional AuthZed Cloud.

**When to skip:** Simple role matrices or static policy bundles are enough. Use **[[RBAC]]** patterns or **[[Open Policy Agent]]** with **[[Policy as Code]]** instead. **[[Keto]]** may fit if you already standardize on Ory.

**Key features:** SpiceDB schema language, gRPC and HTTP APIs, pluggable backends (PostgreSQL, CockroachDB, Spanner, MySQL), Prometheus and OpenTelemetry hooks.

## Details

| Topic | Notes |
|-------|--------|
| **Model** | ReBAC tuples and graph traversal; complements policy engines rather than replacing them |
| **Ops** | Self-host SpiceDB or use AuthZed managed service; pick datastore per scale and HA needs |
| **Ecosystem** | Client libraries, `zed` CLI, schema playground, and CI validation for authz schemas |

**Compared to [[Open Policy Agent]]**

OPA evaluates Rego policies against JSON inputs. SpiceDB persists relationships and answers permission queries at runtime. Many estates use both: OPA for config and admission gates, SpiceDB for application-level object permissions.

**References**

- [SpiceDB product page](https://authzed.com/spicedb/)
- [SpiceDB documentation](https://authzed.com/docs/spicedb/getting-started/discovering-spicedb)
- [SpiceDB on GitHub](https://github.com/authzed/spicedb)
