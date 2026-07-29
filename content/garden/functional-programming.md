---
title: Functional Programming
date: '2026-06-24'
lastmod: '2026-07-24'
draft: false
keywords:
- Functional Programming
- FP
params:
  aliases:
  - FP
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - software-architecture
---

[Functional Programming](https://en.wikipedia.org/wiki/Functional_programming) is a technique we **adopt** in the garden.

## Summary

**What it is:** A paradigm where functions are first-class values, data is preferably immutable, and side effects sit at the edges of the program. Programs compose small functions (map, filter, reduce, pipelines) instead of mutating shared objects in place.

**Core ideas:** pure functions (same inputs, same outputs), immutability, referential transparency, higher-order functions, and explicit effect boundaries (I/O, logging, persistence). Modern FP in industry is often **pragmatic**: impure shell around a pure core, not a ban on all mutation.

**When to use:** ETL and analytics pipelines, event transforms, validation layers, parallel and concurrent workers, configuration transforms, and DSL-style business rules. Strong fit in languages with good FP support (Haskell, Clojure, Elixir, F#, Rust iterators, JavaScript/TypeScript with discipline).

**When to pull back:** Rich UI state machines, ORM-heavy CRUD with identity lifecycles, and teams that lack FP idioms may ship faster with **[[Object-Oriented Programming]]** first. Do not rewrite working OOP services into point-free style without a measured pain point.

**Garden links:** **[[Declarative Programming]]** overlaps on desired outcomes and query-style logic but is broader than FP. **[[First Principles]]** for architecture reviews before paradigm debates.

## Details

### Pillars (Practical Reading)

| Pillar | Practice |
|--------|----------|
| Pure functions | Keep business logic free of hidden I/O and global mutation |
| Immutability | Copy or persist new values; avoid in-place updates in shared data |
| Composition | Build pipelines from small functions with clear types |
| Effects at the edge | Isolate DB, network, and logging in an outer imperative shell |

### Common Failure Modes

- Point-free golf that hides intent from the next maintainer
- Pretending immutability while mutating nested structures in place
- Monadic abstraction before the team understands plain function composition
- FP vs OOP turf wars instead of mixing paradigms by module

### Language Notes

- **Haskell / PureScript:** Strong static guarantees; steeper hiring and tooling curve.
- **[[Clojure]] / Elixir:** Practical FP on the JVM/BEAM with mature concurrency stories. See also **[[cljgo]]** for an experimental Go host.
- **TypeScript / JavaScript:** FP patterns (immutable updates, `map`/`filter`) without a enforced type system; discipline required.
- **Rust:** Ownership plus iterators give many FP benefits without a purely functional style.
- **Go:** First-class functions and small packages; idiomatic Go stays imperative at the edges.

### Related Garden Items

- **[[Object-Oriented Programming]]** for entity-centric domain models and polymorphic boundaries
- **[[Declarative Programming]]** for desired-state specs and query languages where control flow is implicit
- **[[First Principles]]** for choosing structure before paradigm labels
