---
title: Microservices
date: '2026-07-01'
lastmod: '2026-07-07'
draft: false
keywords:
- Microservices
params:
  garden:
    kind: item
    usefulness: hold
    category: technique
    movement: No Change
    subcategories:
    - software-architecture
---

[Microservices](https://martinfowler.com/articles/microservices.html) is a technique we **hold** in the garden.

## Summary

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

### Compared to a Modular Monolith

A modular monolith proves module seams inside one process before you accept network failure modes. Microservices force those seams on day one. Wrong seams mean duplicated logic, sagas, and cross-service refactors that cost more than the original split saved.

Use microservices when independent scaling, failure isolation, or polyglot stacks are documented requirements. Use a modular monolith when the pain is ownership and coupling inside one codebase.

### Org and Conway's Law

Microservices work best when team boundaries already match service boundaries. A siloed org can absorb the coordination cost. A cross-functional product team on a fresh microservice stack often replicates data, fights shared concerns, and loses velocity on platform glue.

### Developer Experience

Local development needs many services, stubs, or heavy compose stacks. Debugging spans traces and repos. Contract changes ripple through consumers. These costs are real even when each service looks simple alone.

### Boundary Discipline

Pair service splits with **[[Common Closure Principle]]** thinking. Split on change drivers, not technical layers. If a boundary cannot survive as a module inside one deployable, it is unlikely to survive as a service without pain.

### Related Garden Items

- **[[Modular Monolith]]** (**trial**) as the default shape before distribution
- **[[Software Architecture]]** subcategory for sibling structural techniques
- **[[First Principles]]** when debating monolith vs microservices defaults
- **[[RPC]]** (**hold**) and **[[gRPC]]** (**assess**) for integration style after you already chose distribution

### References

- Martin Fowler, [Microservices](https://martinfowler.com/articles/microservices.html)
- Sam Newman, *Building Microservices* (O'Reilly)
- Kamil Grzybek, [Modular Monolith: A Primer](https://kamilgrzybek.com/blog/posts/modular-monolith-primer)
