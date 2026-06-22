---
title: "NoSQL"
date: 2026-05-28
lastmod: 2026-06-22
draft: false

keywords:
  - NoSQL

params:
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: "New"
aliases:
  - /radar/techniques/nosql
---

[NoSQL](https://en.wikipedia.org/wiki/NoSQL)

NoSQL ("Not Only SQL") names data stores that model and scale outside classic relational tables. Document, key-value, wide-column, and graph systems each trade different consistency and query patterns. We **assess** the family when requirements clearly need that shape; default to **[[Postgres]]** (adopt) until relational limits show up in production.

## Blurb

> NoSQL databases are designed to handle large volumes of unstructured, semi-structured, or structured data, and they often prioritize scalability, flexibility, and performance over strict consistency.

## Summary

**What it is:** A design space, not one product. Examples include [[MongoDB]] (document), [[Redis]] (key-value), [[Cassandra]] (wide-column), and [[Neo4j]] (graph). **[[usql]]** and BI tools may connect to several of these alongside SQL engines.

**When to use:** Schema churn or nested documents dominate; extreme horizontal write scaling; TTL-heavy caches; graph traversals are the core query pattern.

**When to skip:** Most business apps with joins, transactions, and reporting on a stable schema (**[[Postgres]]**). Analytics warehouses (**[[BigQuery]]**) when SQL over huge columnar data is the real need, not document flexibility.

**Key tradeoffs:** Eventual consistency models, operator skill split, and operational sprawl when every service picks a different engine.


## Details

| Style | Typical use | Relational alternative |
|-------|-------------|------------------------|
| **Document** | CMS, catalogs | Postgres JSONB |
| **Key-value** | Session cache | Redis with Postgres source of truth |
| **Wide-column** | High-ingest time series | Partitioned Postgres or warehouse |
| **Graph** | Identity graphs | Postgres recursive CTEs or dedicated graph DB |

**Practices:** Prove you outgrew Postgres JSONB or replicas before adding a second datastore; standardize on one document store per org if you must; keep **[[Redash]]** queries read-only.

**References**

- [NoSQL (Wikipedia)](https://en.wikipedia.org/wiki/NoSQL)
- [MongoDB NoSQL explained](https://www.mongodb.com/resources/basics/databases/nosql-explained)
