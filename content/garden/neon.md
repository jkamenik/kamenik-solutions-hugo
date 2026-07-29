---
title: Neon
date: '2026-07-23'
lastmod: '2026-07-23'
draft: false
keywords:
- Neon
- Neon Postgres
- Neon Database
params:
  aliases:
  - Neon Postgres
  - Neon Database
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
---

[Neon](https://neon.com/) is serverless **[[Postgres]]** with separated storage and compute, scale-to-zero, and instant database branching. We **trial** it for app and agent backends that need real Postgres without always-on capacity planning.

## Blurb

> Neon is the Postgres backend designed for apps and agents.

## Summary

**What it is:** Managed (and open-source) Postgres platform. Compute is ephemeral; storage is distributed and versioned. Copy-on-write branches give isolated DBs in seconds. Founded by Postgres committers. Databricks company since May 2025. Full Postgres compatibility for drivers, ORMs, and extensions.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Agent / CI databases | Branch per agent, PR, or test run; tear down cheaply |
| Variable traffic | Autoscaling and scale-to-zero vs fixed RDS-sized instances |
| Shared logical catalogs | Many small Postgres roles/DBs on shared infra (e.g. **[[DuckLake]]** metadata) |
| Dev/prod parity | Branch from prod-like data without full clones |

**When to skip:**

- Strict on-prem or air-gapped Postgres only
- Workloads that need a specific cloud's proprietary Postgres fork features
- Teams already happy on a single always-on **[[Postgres]]** (RDS/Cloud SQL) with stable load

**Trade-offs:** True Postgres wire protocol and SQL. Cold starts and branch semantics need app awareness. Vendor is now under Databricks; watch pricing and roadmap coupling to the lakehouse stack.

## Details

### Architecture (short)

| Piece | Role |
|-------|------|
| Compute | Stateless Postgres nodes |
| Pageserver | Durable page storage |
| Safekeepers | Redundant WAL until durable in storage |

Scaling starts more compute; it does not resize a monolithic VM the classic way. Serverless, scale-to-zero Postgres fits many logical catalogs on shared infra without a dedicated instance per tenant.

### Related Garden Items

- **[[Postgres]]** - underlying engine and garden **adopt** default
- **[[DuckLake]]** - SQL catalog format that can sit on Neon-hosted Postgres
- **[[FoundationDB]]** - heavier distributed metadata alternative when you need a shared multi-tenant KV control plane

### References

- [Neon homepage](https://neon.com/)
- [Why Neon? (docs)](https://neon.com/docs/get-started/why-neon)
- [GitHub: neondatabase/neon](https://github.com/neondatabase/neon)
