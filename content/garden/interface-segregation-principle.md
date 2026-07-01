---
title: Interface Segregation Principle
date: '2026-06-24'
lastmod: '2026-06-24'
draft: false
keywords:
- Interface Segregation Principle
- ISP
- Interface Segregation
params:
  aliases:
  - ISP
  - Interface Segregation
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: New
    subcategories:
    - software-architecture
---

[Interface Segregation Principle](https://en.wikipedia.org/wiki/Interface_segregation_principle)

The [Interface Segregation Principle](https://en.wikipedia.org/wiki/Interface_segregation_principle) (ISP) says clients should not depend on methods they do not use. Split fat interfaces into smaller, role-specific contracts. We **adopt** it at API, service, and module boundaries where implementers are forced to no-op or throw on unused operations. It is the **I** in **[[SOLID Principles]]**.

## Blurb

> No client should be forced to depend on methods it does not use.

## Summary

**What it is:** A contract-sizing rule. Prefer several focused interfaces over one "god interface" that every implementer must satisfy in full. Callers depend only on the surface they actually need.

**Why it matters:** Fat interfaces couple unrelated clients to each other. Changing one method signature forces every implementer to redeploy, even those that never called it. Empty stub methods and `NotImplemented` throws are smell.

**When to use:** Plugin APIs, repository layers, RPC services, and public SDKs where multiple consumers share a type but use different subsets. Review any interface with more than one logical role.

**When to pull back:** A single cohesive abstraction with one implementer and one caller does not need splitting yet. Do not fragment interfaces until you see unused method pressure or stub implementations.

**Relation to siblings:** **[[Single Responsibility Principle]]** narrows classes. ISP narrows interfaces. **[[Dependency Inversion Principle]]** works best when ports are small enough that adapters implement only what they need.

## Details

### Signs of Violation

| Signal | Likely fix |
|--------|------------|
| Implementer leaves methods empty or throwing | Split interface by role |
| Callers import a type but use one method | Extract a narrower port |
| Interface name contains "And" or "Manager" | Decompose by change driver |
| Every new feature adds to the same interface | Group by client, not by entity |

### Segregation Tactics

- **Role interfaces:** `Reader` and `Writer` instead of one `Repository` with unused CRUD
- **Consumer-defined ports:** Go-style small interfaces at the call site
- **Adapter per client:** One facade per use case, not one mega-service contract
- **Composition:** A type may implement multiple small interfaces when it truly plays every role

### Common Failure Modes

- One interface per class reflex (ceremony without consumer-driven design)
- Splitting so fine that discovery and navigation suffer
- ISP used to justify duplicate DTOs with no shared core
- Breaking **[[Liskov Substitution Principle]]** when a "segregated" subtype drops required behavior

### Related Garden Items

- **[[Open-Closed Principle]]** for extension points that should stay small at the boundary
- **[[Dependency Inversion Principle]]** for depending on abstractions once ports are right-sized
- **[[Common Reuse Principle]]** for component-level "depend only on what you use"
- **[[Design Pattern]]** for Facade and Adapter when bridging segregated contracts
