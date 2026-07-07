---
title: Interface Segregation Principle
date: '2026-06-24'
lastmod: '2026-07-02'
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
    movement: No Change
    subcategories:
    - software-architecture
---

[Interface Segregation Principle](https://en.wikipedia.org/wiki/Interface_segregation_principle) is a technique we **adopt** in the garden.

## Summary

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

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
