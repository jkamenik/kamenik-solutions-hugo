---
title: Data Access Object
date: '2026-07-01'
lastmod: '2026-07-29'
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

[Data Access Object](https://en.wikipedia.org/wiki/Data_access_object). Is a **[[Design Pattern]]** that hides persistence behind an interface so domain code does not depend on SQL or driver details.

## Summary

**Garden stance:** We **assess** Data Access Object for our estate.

**Key points:**

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
