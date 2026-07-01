---
title: Object-Oriented Programming
date: '2026-06-24'
lastmod: '2026-07-01'
draft: false
keywords:
- Object-Oriented Programming
- OOP
params:
  aliases:
  - OOP
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - software-architecture
    - design-pattern
---

[Object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming) (OOP) organizes code around objects that bundle data with the behavior that operates on it. We **adopt** it as the default mental model for domain modeling in object-capable languages (Java, C#, Python, TypeScript, and similar). Use **[[Design Pattern]]** names after the shape is clear, not as a starting checklist. Keep modules narrow with **[[Single Responsibility Principle]]** and favor composition over deep inheritance trees.

## Blurb

> Object-oriented programming (OOP) is a programming paradigm based on the concept of "objects", which can contain data and code: data in the form of fields (often known as attributes or properties), and code in the form of procedures (often known as methods).

## Summary

**What it is:** A paradigm where state and behavior live together in objects, usually behind interfaces or classes. Objects collaborate through messages (method calls) rather than shared mutable globals.

**Core ideas:** encapsulation (hide internals), abstraction (expose a stable surface), inheritance or subtyping (reuse and polymorphism), and polymorphism (one interface, many implementations). Modern style stresses **composition over inheritance** and small objects with clear contracts.

**Discipline:** OOP pairs naturally with indirect control flow. Factories, interfaces, and dependency injection move callers away from concrete types. Treat **[[Dependency Inversion Principle]]** as required when objects collaborate across module boundaries.

**OOP is not one shape:** Languages implement objects differently. Classical OOP uses explicit classes and encapsulation (the Java and Python mental model). Composable or duck-typed OOP accepts substitutes when behavior matches (**[[GoLang]]**, **[[Ruby]]**). Prototypal OOP chains objects through prototypes rather than class templates (**[[JavaScript]]**).

**When to use:** Business domains with rich entities, UI models, SDKs, and services where boundaries map naturally to nouns and lifecycles. Strong fit when the language and ecosystem assume OOP (Spring, .NET, enterprise Java).

**When to pull back:** Pipelines, ETL, and data transforms often read clearer as functions over immutable data. Infrastructure glue and one-off scripts rarely need class hierarchies. If a **[[Design Pattern]]** adds layers without removing duplication, simplify first.

**Garden links:** **[[First Principles]]** for architecture reviews before pattern shopping. **[[Design Pattern]]** for named structural choices after constraints are clear. **[[Dependency Inversion Principle]]** for stable boundaries between layers.

## Details

### Pillars (Practical Reading)

| Pillar | Practice |
|--------|----------|
| Encapsulation | Expose behavior; keep invariants inside the object |
| Abstraction | Depend on interfaces, not concrete types, at boundaries |
| Polymorphism | Swap implementations without rewriting callers |
| Composition | Prefer has-a over is-a when behavior mixes |

### OOP Flavors

| Style | Mechanism | Typical languages |
|-------|-----------|-------------------|
| Classical | Classes, encapsulation, inheritance | Java, Python |
| Composable | Structs or objects plus interfaces; duck typing | **[[GoLang]]**, **[[Ruby]]** |
| Prototypal | Prototype chains; instances inherit from objects | **[[JavaScript]]** |

Classical OOP is what most teams picture first. Composable styles still use objects but swap implementations when behavior fits, without a shared class hierarchy. In prototypal **[[JavaScript]]**, built-ins such as `Array` are constructor functions. Literal arrays are instances whose prototype chain includes `Array.prototype`.

### Common Failure Modes

- God objects that know every subsystem
- Deep inheritance chains that encode business rules in parent classes
- Anemic models (data bags with logic scattered in services)
- Pattern-first design (factories and abstract factories before a second use case exists)
- Skipping **[[Dependency Inversion Principle]]** and wiring callers directly to concrete types

### Language Notes

- **Java / C# / TypeScript:** OOP is the default idiom; lean on interfaces and small classes.
- **Python:** OOP is available but optional; use classes when they clarify state, not by reflex.
- **Go:** Structs and interfaces favor composition; avoid forcing Java-style hierarchies.
- **Ruby:** Duck typing and modules mix behavior without deep inheritance trees.
- **JavaScript:** Prototypal inheritance and object literals; prefer composition and factory functions over class sprawl when ES classes are not required.

### Related Garden Items

- **[[Single Responsibility Principle]]** for one-reason-to-change module boundaries
- **[[Dependency Inversion Principle]]** for stable abstractions at module boundaries
- **[[Design Pattern]]** subcategory for GoF-style and idiomatic pattern items
- **[[Declarative Programming]]** for desired-state and query-style problems where OOP is a poor fit
- **[[Functional Programming]]** for immutable pipelines and transforms where shared mutable objects add risk
