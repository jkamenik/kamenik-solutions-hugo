---
title: Data Access Object
date: '2026-07-01'
lastmod: '2026-07-01'
draft: false
keywords:
- Data Access Object
- DAO
params:
  aliases:
  - DAO
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: No Change
    subcategories:
    - design-pattern
---

[Data Access Object (DAO)](https://en.wikipedia.org/wiki/Data_access_object) is a **[[Design Pattern]]** that hides persistence behind an interface so domain code does not depend on SQL or driver details. We **assess** it per service as the thin layer between business logic and storage. Pair DAOs with explicit schema migrations (**[[Sqitch]]** or similar) instead of leaning on **[[ORM]]** for both mapping and DDL. The same seam works for databases, files, and remote services when callers need stable load and save semantics.

## Blurb

> In software, a data access object (DAO) is a pattern that provides an abstract interface to some type of database or other persistence mechanism. By mapping application calls to the persistence layer, the DAO provides data operations without exposing database details.

## Summary

**What it is:** A persistence-facing object or module with a narrow public API (load, save, delete, query) and I/O code behind it. Callers work with domain types or DTOs; the DAO translates to tables, rows, files, or wire formats.

**Why it matters:** Separates data access from business rules (**[[Single Responsibility Principle]]**). The backing store can change without rewriting services, as long as the DAO contract stays stable. That swap is the main payoff: SQL today, another engine, filesystem, or remote API tomorrow.

**Storage abstraction:** DAO is not database-only. Use the same pattern for relational stores, filesystem layout, object stores, and remote HTTP or RPC services. **[[Dependency Inversion Principle]]** applies: domain code depends on the DAO interface, not the concrete backend.

**Serialization:** When domain state must be encoded for persistence, cache, or handoff between processes, keep serialize and deserialize inside the DAO. Callers pass objects; the DAO owns format and transport details.

**When to use:** Services that outgrow framework-default **[[ORM]]** magic, teams that want SQL in one place, and **[[Object-Oriented Programming]]** stacks where test doubles for storage speed up unit tests. Strong fit when you may swap storage or add a second backend behind the same interface.

**When to pull back:** Simple CRUD apps where the framework ORM already ships migrations and the team reads generated SQL confidently. Analytics paths where **[[dbt-core]]** or warehouse SQL owns the model. Do not mirror every table with a DAO before the domain shape is clear.

**Relation to other patterns:** Fowler's Table Data Gateway and Repository overlap in practice. DAO is the Java EE term for a gateway-style persistence seam. **[[ORM]]** can implement DAO interfaces internally; the garden stance is to keep the seam explicit even when a library helps.

## Details

| Topic | Notes |
|-------|--------|
| **Typical API** | `findById`, `save`, `delete`, list/query methods scoped to one aggregate or table group |
| **Implementation** | Raw SQL + driver, query builder, or ORM session hidden inside the DAO class |
| **Testing** | Swap DAO for in-memory or fake implementation; keep domain tests free of a live DB when possible |
| **Migrations** | DDL lives in **[[Sqitch]]** (or Flyway-style tools), not scattered in DAO methods |

### Backends

| Backend | DAO hides |
|---------|-----------|
| **Database** | SQL, parameters, connection handling, row mapping |
| **Filesystem** | Paths, directories, open/read/write, permissions |
| **Remote service** | HTTP/gRPC clients, retries, auth, response parsing; same-host daemons via **[[IPC]]** |
| **Serialized state** | JSON, protobuf, or other encode/decode at the boundary |

Swap backends by replacing the DAO implementation while keeping the interface stable. Domain services should not branch on storage type.

### Common Shapes

| Style | Scope | Trade-off |
|-------|-------|-----------|
| One DAO per table | Thin CRUD around a single table | Simple; joins may leak into services |
| One DAO per aggregate | Root entity plus related rows | Clearer domain boundary; more custom SQL |
| Generic DAO | Reusable CRUD base class | Fast start; tends toward anemic queries |

### Failure Modes

- DAO becomes a dumping ground for every query in the system
- Interface mirrors the database schema one-to-one while the domain model diverges
- "DAO" label on top of a full **[[ORM]]** with no real abstraction boundary
- Missing transaction boundaries when multiple DAO calls must commit together
- Serialization logic scattered in services instead of centralized in the DAO

### Related Garden Items

- **[[ORM]]** for full object-graph mapping vs explicit DAO SQL
- **[[Sqitch]]** for versioned deploy, revert, and verify scripts
- **[[Object-Oriented Programming]]** for how services compose with persistence ports
- **[[Dependency Inversion Principle]]** when domain code depends on DAO interfaces, not drivers
