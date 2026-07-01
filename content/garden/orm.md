---
title: Object-Relational Mapping (ORM)
date: '2025-12-12'
lastmod: '2026-07-01'
draft: false
keywords:
- Object-Relational Mapping (ORM)
- Object-relational Mapping
params:
  aliases:
  - Object-relational Mapping
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: No Change
    subcategories:
    - software-architecture
---

[Object-relational mapping (ORM)](https://en.wikipedia.org/wiki/Object%E2%80%93relational_mapping) bridges **[[Object-Oriented Programming]]** domain objects and relational database tables. We **assess** ORMs per service because they speed CRUD-heavy apps but hide SQL cost, schema migration, and query shape. Default to explicit data access when performance or reporting dominates.

## Blurb

> Object-relational mapping is a programming technique for converting data between incompatible type systems using object-oriented programming languages.

## Summary

**What it is:** a library or framework that maps classes to tables, relationships to joins, and object graphs to queries (Hibernate, Entity Framework, SQLAlchemy, ActiveRecord, Prisma-style layers, and similar).

**When it helps:** CRUD services, admin apps, and **[[MVC]]** models where schema and object model align and teams value productivity over hand-tuned SQL.

**When to pause:** hot paths with complex joins, batch/reporting workloads, heavy aggregation, or teams that cannot explain generated SQL. Leaky abstractions (N+1 queries, lazy-load surprises, migration drift) are the usual failure mode.

**Garden stance:** ORM is a technique choice, not a moral default. Pair with migrations, query review in CI, and escape hatches to raw SQL where needed.

## Details

| Topic | Notes |
|-------|--------|
| **Strengths** | Faster feature work, typed models, migration tooling in mature stacks |
| **Risks** | Hidden queries, schema/object drift, difficult performance tuning |
| **Mitigations** | Explicit fetch plans, query logging in dev, DTOs at API boundaries |
| **Alternatives** | Query builders, repository + raw SQL, **[[dbt-core]]** for analytics paths |
| **Common pairing** | **[[MVC]]** model layer; **[[Postgres]]** as typical backing store |

### Decision Checklist

1. Can the team read and optimize the SQL the ORM emits?
2. Are relationships stable enough to map cleanly to objects?
3. Is most access CRUD-shaped rather than analytic?
4. If any answer is no, prefer thinner mapping or SQL-first access for that bounded context.
