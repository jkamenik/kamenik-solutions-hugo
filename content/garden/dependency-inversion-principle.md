---
title: Dependency Inversion Principle
date: '2026-06-24'
lastmod: '2026-06-24'
draft: false
keywords:
- Dependency Inversion Principle
- DIP
- Dependency Inversion
params:
  aliases:
  - DIP
  - Dependency Inversion
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - software-architecture
---

[Dependency Inversion Principle](https://en.wikipedia.org/wiki/Dependency_inversion_principle)

The [Dependency Inversion Principle](https://en.wikipedia.org/wiki/Dependency_inversion_principle) (DIP) is the **D** in **[[SOLID Principles]]**. High-level policy should not depend on low-level details; both should depend on abstractions. We **adopt** it wherever modules need to swap implementations, mock collaborators in tests, or keep domain logic free of framework imports. DIP is a design rule, not the same thing as dependency injection (a wiring technique).

## Blurb

> 1. High-level modules should not depend on low-level modules. Both should depend on abstractions.
> 2. Abstractions should not depend on details. Details should depend on abstractions.

## Summary

**What it is:** A coupling rule. Callers and callees meet at interfaces (or abstract types), not at concrete classes. The domain layer defines the ports it needs; infrastructure adapters implement them.

**Why it matters:** Without inversion, a service imports a specific database driver, HTTP client, or SDK. Every test drags real IO. Every vendor swap rewrites business code. DIP pushes volatile details behind stable abstractions.

**When to use:** Service boundaries, repository layers, plugin systems, and any code you want to unit test without containers or cloud APIs. Natural fit with **[[Object-Oriented Programming]]** and **[[Design Pattern]]** choices like Strategy and Adapter.

**When to pull back:** Scripts, one-off CLIs, and throwaway prototypes where a single concrete dependency is fine. Do not add interface layers before a second implementation or a test seam is real.

**Not the same as dependency injection:** Injection is how you supply implementations at runtime (constructor args, DI containers). DIP is why you introduce the abstraction in the first place.

## Details

### Rules in Practice

| Rule | Practice |
|------|----------|
| Depend on abstractions | Domain code imports interfaces, not `PostgresClient` or `S3Bucket` |
| Details depend inward | Infrastructure projects reference domain ports, not the reverse |
| Stable abstractions | Port shapes change rarely; adapters absorb vendor churn |

### Common Failure Modes

- Leaky abstractions that mirror one vendor's API one-to-one
- Interface-per-class ceremony with only one implementation ever
- "Inversion" that still lets frameworks own the domain model
- Confusing DIP with a DI framework requirement

### Testing and Delivery

- **[[Unit Testing]]** gets easier when collaborators are interfaces you can fake or stub
- Keep composition roots (main, wiring modules) as the only place that picks concrete types
- In Go, small interfaces defined by the consumer are idiomatic DIP without inheritance

### Related Garden Items

- **[[Single Responsibility Principle]]** for narrowing what each module owns
- **[[Interface Segregation Principle]]** for keeping ports small enough to implement cleanly
- **[[Object-Oriented Programming]]** for the paradigm DIP most often supports
- **[[Design Pattern]]** for Adapter, Strategy, and similar structural choices after ports are clear
