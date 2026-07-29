---
title: OLTP
date: '2026-07-23'
lastmod: '2026-07-23'
draft: false
keywords:
- OLTP
- Online Transaction Processing
- Online transaction processing
params:
  aliases:
  - Online Transaction Processing
  - Online transaction processing
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: New
    subcategories:
    - software-architecture
---

[OLTP](https://en.wikipedia.org/wiki/Online_transaction_processing) (Online Transaction Processing) is the approach of processing many short, concurrent read/write transactions against current operational data. We **adopt** it as the default vocabulary for systems of record versus **[[OLAP]]**.

## Blurb

> Online transaction processing (OLTP) is a type of database system used in transaction-oriented applications, such as many operational systems.

## Summary

**What it is:** Write-heavy (and mixed) workloads that keep the live business state correct: orders, payments, inventory, sessions, tickets. Queries are usually simple, selective, and latency-sensitive. Integrity, concurrency control, and durability matter more than multi-dimensional roll-ups.

**When to use:**

| Situation | Notes |
|-----------|--------|
| System of record | App databases, ledgers, booking, auth stores |
| High concurrency writes | Many users mutating small rows at once |
| Strong consistency needs | ACID transactions on current state (**[[Postgres]]**, **[[Neon]]**) |
| Operational APIs | CRUD backends behind product features |

**When to skip:**

- Historical analytics, BI, and large scans (**[[OLAP]]**, warehouses, lakes)
- Calling a warehouse an OLTP store when writes are rare batch loads
- Using an analytic engine as the primary mutable app database

**Trade-offs:** Excellent for correct, concurrent updates; poor fit for heavy aggregations over years of history without a separate analytic path.

## Details

### OLTP Vs **[[OLAP]]**

| Topic | OLTP | OLAP |
|-------|------|------|
| Workload | Many small transactions | Complex reads, aggregates |
| Data shape | Current, often normalized | Historical, denormalized or columnar |
| Optimization | Indexes, write path, integrity | Scan, compress, columnar |
| Garden examples | **[[Postgres]]**, **[[Neon]]** | **[[DuckDB]]**, **[[Snowflake]]**, **[[BigQuery]]** |

### Design Notes

| Topic | Notes |
|-------|--------|
| Transactions | Prefer clear ACID boundaries over ad-hoc multi-statement hope |
| Scaling | Vertical + careful sharding; or serverless Postgres (**[[Neon]]**) for bursty apps |
| Consistency | Pair with **[[CAP Theorem]]** when the store is multi-region |
| Escape hatches | **[[NoSQL]]** when the access pattern is not relational CRUD |

### Related Garden Items

- Engines: **[[Postgres]]**, **[[Neon]]**
- Contrast: **[[OLAP]]** for analytic workloads
- Distributed trade-offs: **[[CAP Theorem]]**

### References

- [Wikipedia: Online transaction processing](https://en.wikipedia.org/wiki/Online_transaction_processing)
- Companion technique: **[[OLAP]]**
