---
title: Iceberg
date: '2026-07-23'
lastmod: '2026-07-23'
draft: false
keywords:
- Iceberg
- Apache Iceberg
params:
  aliases:
  - Apache Iceberg
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: New
---

[Apache Iceberg](https://iceberg.apache.org/) is an open table format for huge analytic datasets on object storage. We **trial** it as the default multi-engine lakehouse table format when the estate needs Spark, Trino, Flink, and friends on the same tables.

## Blurb

> The open table format for analytic datasets.

## Summary

**What it is:** High-performance table format with SQL-friendly semantics: schema evolution, hidden partitioning, time travel, rollback, and compaction. Engines (**[[Trino]]**, Spark, Flink, Hive, Impala, and others) can share tables safely. Data files are typically **[[Parquet]]** (or similar) on the lake.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Multi-engine lakes | Several query engines on one catalog of tables |
| Large mutable analytics | Merge, update, delete with snapshots |
| Open lakehouse standard | Broad vendor and OSS adoption |

**When to skip:**

- Single-engine embedded lakes where **[[DuckLake]]** SQL metadata is simpler
- Tiny datasets that never leave **[[DuckDB]]** or a warehouse
- No appetite for catalog services and compaction ops

**Trade-offs:** Mature ecosystem and engine support; metadata design still involves file-based snapshots plus a catalog for atomicity. Ops and planning latency are the usual pain points vs SQL-catalog formats.

## Details

### Capabilities (short)

| Feature | Notes |
|---------|--------|
| Schema evolution | Add, rename, reorder without rewrite zombies |
| Hidden partitioning | Engines skip files without manual partition filters |
| Time travel | Query by snapshot or timestamp |
| Compaction | Rewrite strategies built in |

### Vs **[[DuckLake]]**

Iceberg keeps much metadata in files and uses a catalog for version pointers. DuckLake puts all metadata in SQL. Prefer Iceberg for multi-engine interoperability today; assess DuckLake when the stack is DuckDB/Postgres-centric and early-format risk is acceptable.

### References

- [iceberg.apache.org](https://iceberg.apache.org/)
