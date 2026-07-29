---
title: OLAP
date: '2026-07-23'
lastmod: '2026-07-23'
draft: false
keywords:
- OLAP
- Online Analytical Processing
- Online analytic processing
params:
  aliases:
  - Online Analytical Processing
  - Online analytic processing
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: New
    subcategories:
    - software-architecture
---

[OLAP](https://en.wikipedia.org/wiki/Online_analytical_processing) (Online Analytical Processing) is the approach of answering multi-dimensional analytical queries fast over large historical datasets. We **adopt** it as the default vocabulary for warehouses, lakes, and embedded analytic engines versus **[[OLTP]]**.

## Blurb

> In computing, online analytical processing (OLAP) (/ˈoʊlæp/), is an approach to quickly answer multi-dimensional analytical (MDA) queries.

## Summary

**What it is:** Read-heavy analytics pattern for BI, forecasting, and ad-hoc SQL over fact data. Classic ops include roll-up, drill-down, and slice/dice across dimensions (time, product, region, and so on). Contrasts with **[[OLTP]]**, which optimizes high-volume insert/update/delete of current records.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Warehouses and lakes | **[[Snowflake]]**, **[[BigQuery]]**, **[[Trino]]**, **[[Iceberg]]** / **[[DuckLake]]** |
| Embedded analytics | **[[DuckDB]]** and similar in-process engines |
| Columnar storage | **[[Parquet]]**, **[[Arrow]]** layouts favor scan and aggregate |
| Reporting and planning | Sales, finance, ops metrics over history |

**When to skip:**

- High-throughput transactional systems of record (**[[Postgres]]** as **[[OLTP]]**, payment ledgers)
- Low-latency single-row lookups as the primary workload
- Calling every SQL database "OLAP" when the real need is CRUD

**Trade-offs:** Excellent for aggregates and historical analysis; poor fit as the system of record for mutable operational state. Modern "cloud OLAP" often uses columnar SQL engines rather than classic MOLAP cubes alone.

## Details

### OLAP Vs **[[OLTP]]**

| Topic | OLAP | OLTP |
|-------|------|------|
| Workload | Complex reads, aggregates | Many small transactions |
| Data shape | Historical, denormalized or star/cube | Current, normalized |
| Optimization | Scan, compress, columnar | Indexes, write path, integrity |
| Garden examples | **[[DuckDB]]**, **[[Snowflake]]**, **[[BigQuery]]** | **[[Postgres]]** as app DB |

### Classic Vs Modern Shapes

| Shape | Notes |
|-------|--------|
| MOLAP | Multidimensional cubes (classic OLAP servers) |
| ROLAP | Analytical SQL over relational stores |
| HOLAP | Hybrid of cube and relational |
| Cloud / lake OLAP | Separated storage/compute; **[[Parquet]]** + table formats |

### Related Garden Items

- Engines: **[[DuckDB]]**, **[[Snowflake]]**, **[[BigQuery]]**, **[[Trino]]**
- Formats: **[[Parquet]]**, **[[Arrow]]**, **[[Iceberg]]**, **[[DuckLake]]**
- Contrast: **[[OLTP]]** / **[[Postgres]]** for transactional systems of record

### References

- [Wikipedia: Online analytical processing](https://en.wikipedia.org/wiki/Online_analytical_processing)
- [IBM: What is OLAP?](https://www.ibm.com/think/topics/olap)
