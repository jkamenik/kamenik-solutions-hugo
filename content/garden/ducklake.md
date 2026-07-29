---
title: DuckLake
date: '2026-07-23'
lastmod: '2026-07-23'
draft: false
keywords:
- DuckLake
- Duck Lake
params:
  aliases:
  - Duck Lake
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
---

[DuckLake](https://ducklake.select/manifesto/) is an open lakehouse format that keeps table data in **[[Parquet]]** (and kin) on object storage, and puts all catalog metadata in a normal SQL database. We **assess** it as a simpler alternative to **[[Iceberg]]**/Delta-style file mazes when a SQL catalog is already in the stack.

## Blurb

> DuckLake simplifies lakehouses by using a standard SQL database for all metadata, instead of complex file-based systems, while still storing data in open formats like Parquet. This makes it more reliable, faster, and easier to manage.

## Summary

**What it is:** Open table format from the **[[DuckDB]]** authors (Mark Raasveldt, Hannes Mühleisen). Metadata lives in portable SQL tables with ACID transactions. Data files stay on blob storage. Any ACID SQL engine with primary keys can host the catalog (**[[Postgres]]**, DuckDB, and others).

**When to use:**

| Situation | Notes |
|-----------|--------|
| Lakehouse + SQL catalog | You already run Postgres or DuckDB and want open Parquet data |
| Multi-table transactions | Cross-table ACID and transactional DDL in one catalog |
| Agent / differential testing | Independent DuckDB `ducklake` reader as an oracle against another engine |
| Laptop-to-cloud path | Local DuckDB file catalog first; migrate catalog DB without moving data files |

**When to skip:**

- Org standardized on Iceberg or Delta with mature catalogs and tooling
- Need for a format with broad multi-engine production adoption today (DuckLake is early)
- No willingness to operate a catalog SQL database

**Trade-offs:** Cleaner than JSON/Avro snapshot trees once a DB is in the path anyway. Younger ecosystem than Iceberg. Catalog DB becomes a scaling and availability concern (by design, same pattern as BigQuery/Spanner and Snowflake/**[[FoundationDB]]** metadata).

## Details

### Architecture

| Layer | DuckLake choice |
|-------|-----------------|
| Data | Immutable open files (**[[Parquet]]**) on disk, S3, GCS, Azure, etc. |
| Metadata | Relational tables + SQL transactions in a catalog database |
| Compute | Any engine that speaks the format (DuckDB extension first) |

Three-way split: storage, compute, and metadata. Catalog traffic is orders of magnitude smaller than data IO. Shared **[[Postgres]]** or **[[Neon]]** can back many logical catalogs.

### Vs **[[Iceberg]]** / Delta

Iceberg and Delta encode much metadata in files, then add a catalog DB for atomic version pointers. DuckLake moves *all* metadata into SQL once that DB exists. Fewer small files, faster planning (one catalog query), optional inlining of tiny writes into the catalog DB.

### References

- [DuckLake manifesto](https://ducklake.select/manifesto/)
- Parent engine: **[[DuckDB]]**
