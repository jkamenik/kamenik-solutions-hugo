---
title: FoundationDB
date: '2026-07-23'
lastmod: '2026-07-23'
draft: false
keywords:
- FoundationDB
- FDB
params:
  aliases:
  - FDB
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
---

[FoundationDB](https://www.foundationdb.org/) is an open-source distributed key-value store with ACID transactions. We **assess** it for multi-tenant metadata and control-plane data that needs strong consistency at scale.

## Blurb

> FoundationDB gives you the power of ACID transactions in a distributed database.

## Summary

**What it is:** Ordered key-value core with layers for higher-level data models. Designed to scale out, tolerate faults, and behave like one ACID database. Hardened with deterministic simulation testing. Open-sourced by Apple.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Shared multi-tenant metadata | Global catalog or coordination that must stay strongly consistent |
| Layered data models | Build document, graph, or relational layers on the KV core |
| Extreme fault-injection culture | Teams that will invest in ops expertise and sim-style testing |

**When to skip:**

- Self-hosted or BYOC products where metadata should deploy with the app (**[[Postgres]]** is often enough)
- Teams without capacity to operate a specialized distributed store
- Workloads that fit a single-region relational DB

**Trade-offs:** Industry-proven (Apple, Snowflake metadata stories) but operationally heavy. Expertise is scarce. Wrong default for "ship anywhere" agent-native databases.

## Details

### Ops Reality

FoundationDB is a full distributed system. It needs specialized operators, careful capacity planning, and deep familiarity with its failure modes. That cost is justified for hyperscale shared control planes. It is a poor default when the product must run in customer clouds or as a laptop binary. Prefer **[[Postgres]]** (or **[[Neon]]**) for deployable metadata, including **[[DuckLake]]** catalogs.

### Compared to **[[Postgres]]**

| Topic | FoundationDB | Postgres |
|-------|--------------|----------|
| Consistency model | Distributed ACID KV | Single-primary ACID (or managed HA) |
| Ops surface | Cluster + layers | Familiar RDBMS ops |
| Self-host / BYOC | Hard without specialists | Practical with Neon-style vendors |
| Garden signal | Assess for shared control planes | Prefer for deployable metadata |

### References

- [FoundationDB homepage](https://www.foundationdb.org/)
- [FoundationDB documentation](https://apple.github.io/foundationdb/)
