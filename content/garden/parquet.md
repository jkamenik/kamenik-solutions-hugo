---
title: Parquet
date: '2026-07-23'
lastmod: '2026-07-23'
draft: false
keywords:
- Parquet
- Apache Parquet
params:
  aliases:
  - Apache Parquet
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: New
---

[Apache Parquet](https://parquet.apache.org/) is an open columnar file format for bulk analytic storage and retrieval. We **adopt** it as the default on-disk columnar format for lakes and interchange.

## Blurb

> Apache Parquet is an open source, column-oriented data file format designed for efficient data storage and retrieval. It provides high performance compression and encoding schemes to handle complex data in bulk and is supported in many programming languages and analytics tools.

## Summary

**What it is:** Column-oriented layout with compression and encoding suited to analytics. Wide language and tool support (**[[DuckDB]]**, Spark, **[[Trino]]**, warehouses). Common data layer under **[[Iceberg]]** and **[[DuckLake]]**.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Analytic datasets | Prefer over row-oriented dumps for scan-heavy SQL |
| Lake / lakehouse tables | Standard file format under Iceberg, DuckLake, Delta |
| Interchange | Share large tables without a live database |

**When to skip:**

- Tiny tables and human editing (**[[CSV]]**, **[[JSON]]**)
- Frequent single-row updates (OLTP files or a database)
- Streaming event payloads better kept as JSON/Avro messages

**Trade-offs:** Excellent read efficiency and compression; not ideal for random row updates or hand editing.

## Details

### Related Formats

| Format | Role vs Parquet |
|--------|-----------------|
| **[[CSV]]** | Human-friendly exchange; worse for large analytic scans |
| **[[Arrow]]** | In-memory columnar; Parquet is the common on-disk cousin |
| **[[Iceberg]]** / **[[DuckLake]]** | Table formats that point at Parquet (and kin) data files |

### References

- [parquet.apache.org](https://parquet.apache.org/)
