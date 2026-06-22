---
title: "Postgres"
date: 2026-05-28
lastmod: 2026-06-22
draft: false

keywords:
  - Postgres
  - PostgreSQL

params:
  aliases:
    - PostgreSQL
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: "New"
aliases:
  - /radar/tools/postgres
---

[PostgreSQL](https://www.postgresql.org/) (Postgres) is the world's most advanced open source relational database. It is ACID-compliant, extensible, and runs everywhere from laptops to managed cloud instances. We **adopt** it as the default OLTP and analytics-adjacent store when a relational model fits.

## Blurb

> PostgreSQL is a powerful, open source object-relational database system with over 35 years of active development that has earned it a strong reputation for reliability, feature robustness, and performance.

## Summary

**What it is:** Object-relational engine with SQL, JSONB, extensions (PostGIS, pgvector, and many others), logical replication, and permissive licensing. Same project whether self-hosted, on RDS/Aurora/AlloyDB, or embedded.

**When to use:** New application databases, warehouses that still speak SQL, extensions for geo or vectors, teams that want one engine for transactional and moderate analytics workloads on a replica.

**When to skip:** Petabyte-scale warehouse analytics where a columnar EDW (**[[BigQuery]]**) is already standard. Document-only workloads with no relational joins (**[[NoSQL]]** patterns). Legacy **[[MySQL]]** apps you are not migrating yet.

**Key features:** MVCC, robust indexing, foreign data wrappers, row-level security, mature backup and HA patterns.


## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | Managed (RDS, Cloud SQL, Neon, Supabase) or self-hosted; Helm charts for K8s |
| **Ops** | `pg_dump`, PITR, connection pooling via PgBouncer or pooler in managed offerings |
| **BI** | Native connector in **[[Grafana]]**, **[[Metabase]]**, **[[Redash]]**, **[[Apache Superset]]** |

**Practices:** Migrations with Flyway or similar; read replicas for BI; separate roles for app vs analyst; prefer Postgres over **[[MySQL]]** for greenfield relational work.

**References**

- [PostgreSQL documentation](https://www.postgresql.org/docs/)
- [PostgreSQL License](https://www.postgresql.org/about/licence/)
