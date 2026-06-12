---
title: "MySQL"
date: 2026-05-28
lastmod: 2026-06-12
draft: false

keywords:
  - MySQL

params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: "New"
aliases:
  - /radar/tools/mysql
---

[MySQL](https://www.mysql.com/) is the world's most popular open source relational database, now led by Oracle. It powers countless LAMP-era apps and managed offerings (RDS, Cloud SQL MySQL). We **hold** it: do not start new relational projects on MySQL when **[[Postgres]]** (adopt) is an option.

## Blurb

> MySQL is the world's most popular open source database. With its proven performance, reliability and ease-of-use, MySQL has become the leading database choice for web-based applications.

## Summary

**What it is:** Open source RDBMS with [[InnoDB]] as the default transactional engine, replication, and a large hosting ecosystem. Commercial and community builds share the same SQL surface most developers know.

**When to use:** Maintaining existing MySQL schemas, vendor contracts, or frameworks locked to MySQL. Short-term parity during a migration plan to **[[Postgres]]**.

**When to skip:** Greenfield OLTP or new microservices (use **[[Postgres]]**). Warehouse-scale analytics on GCP (**[[BigQuery]]**). Choosing MySQL only because it was the default a decade ago.

**Hold rationale:** **[[Postgres]]** matches or exceeds MySQL on features, extensions, and licensing clarity for new work. Existing MySQL remains supported; plan moves when touch cost is low.

## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | Oracle MySQL, MariaDB fork, RDS, Cloud SQL |
| **Ops** | Replication lag monitoring; charset and collation audits on legacy schemas |
| **BI** | Supported by **[[Redash]]**, **[[Metabase]]**, and most SQL BI tools |

**Practices:** Treat MySQL as legacy unless a hard constraint blocks migration; document schema diffs before cutover to Postgres; avoid new stored-procedure-heavy designs that increase lock-in.

**References**

- [MySQL documentation](https://dev.mysql.com/doc/)
- [What is MySQL (Oracle)](https://www.oracle.com/mysql/what-is-mysql/)
