---
title: Modular Monolith
date: '2026-07-01'
lastmod: '2026-07-07'
draft: false
keywords:
- Modular Monolith
- Modular Monolith Architecture
params:
  aliases:
  - Modular Monolith Architecture
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - software-architecture
---

[Modular Monolith](https://kamilgrzybek.com/blog/posts/modular-monolith-primer). Kamil Grzybek Personal Site We **adopt** it under **[[Technique]]** in the garden.

## Summary

**What it is:** One deployment unit organized into independent modules. Each module owns its business logic and data access behind a public interface. Other modules call that interface only.

**Why it matters:** You keep monolith ops simplicity (one build, one deploy, one runtime). You still get boundaries that support team ownership and future extraction if a module truly needs its own service.

**When to use:** Single product or platform teams, greenfield apps, and rewrites where microservices would add cost before you have proof of separate scaling or release cadences.

**When to skip:** Large orgs with many unrelated offerings, hard isolation requirements, or teams that already operate mature platform tooling for distributed systems.

| Shape | Deploy units | Boundaries | Typical trade-off |
|-------|--------------|------------|-------------------|
| Traditional monolith | One | Often implicit | Fast start; coupling grows in shared code |
| Modular monolith | One | Explicit modules and contracts | Enforced design; refactor stays in-process |
| Microservices | Many | Network and service contracts | Independent scale and release; distributed complexity |

**Module checklist (Grzybek):** independent and interchangeable; contains everything needed for its capability; exposes a well-defined contract; resists cross-module internal access.

## Details

### Compared to Microservices

Microservices split deployables and force network boundaries early. A modular monolith keeps one process and one release pipeline while you prove module seams. Moving code between modules is a refactor. Promoting a module to a service is a migration with new failure modes.

Use microservices when independent scaling, failure isolation, or polyglot stacks are proven requirements. Use a modular monolith when the main pain is unclear ownership inside one codebase, not cross-service traffic.

### Boundary Enforcement

Module boundaries erode under deadline pressure unless tooling backs them. Common guards:

| Mechanism | Role |
|-----------|------|
| Architecture tests (ArchUnit, NetArchTest, custom lint) | Fail CI on illegal cross-module imports |
| Module-local persistence | No direct queries into another module's tables |
| Public API packages or facades | Only exported types are callable |
| Event or message contracts | Async integration without shared domain models |

### Related Garden Items

- **[[Common Closure Principle]]** for grouping code that changes together into modules
- **[[Single Responsibility Principle]]** for class-level discipline inside each module
- **[[First Principles]]** when debating monolith vs microservices defaults
- **[[Software Architecture]]** subcategory for sibling structural techniques

### References

- Kamil Grzybek, [Modular Monolith: A Primer](https://kamilgrzybek.com/blog/posts/modular-monolith-primer)
- Kamil Grzybek, [Modular Monolith: Architectural Drivers](https://kamilgrzybek.com/blog/posts/modular-monolith-architectural-drivers)
