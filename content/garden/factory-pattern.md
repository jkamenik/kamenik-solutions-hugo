---
title: Factory Pattern
date: '2026-06-24'
lastmod: '2026-06-24'
draft: false
keywords:
- Factory Pattern
- Factory Method Pattern
- Abstract Factory Pattern
params:
  aliases:
  - Factory Method Pattern
  - Abstract Factory Pattern
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: New
    subcategories:
    - design-pattern
---

[Factory Pattern](https://en.wikipedia.org/wiki/Factory_method_pattern)

The [Factory pattern](https://en.wikipedia.org/wiki/Factory_method_pattern) family centralizes object creation behind an interface or function so callers depend on abstractions, not concrete constructors. We **adopt** it when construction logic branches on config, environment, or plugin type and **[[Dependency Inversion Principle]]** needs a stable seam. It supports **[[Open-Closed Principle]]** by adding new product types without editing every call site. Do not introduce a factory hierarchy before a second implementation exists.

## Blurb

> Define an interface for creating an object, but let subclasses decide which class to instantiate. The Factory Method lets a class defer instantiation to subclasses.

## Summary

**What it is:** A creational **[[Design Pattern]]** group. A factory hides `new` (or equivalent) behind a method or object that picks the concrete type. Variants include simple factory functions, Factory Method (subclass chooses), and Abstract Factory (families of related products).

**Why it matters:** Scattered construction couples callers to concrete classes and config parsing. A factory keeps creation in one place. Tests swap factories or pass fakes without rewriting domain code.

**When to use:** Plugin registries, storage backends, transport clients, and parsers selected by runtime config. Natural follow-on once **[[Dependency Inversion Principle]]** defines a port that needs multiple implementations.

**When to pull back:** One type, one constructor, no forecast of variation. A plain function that returns the only implementation is enough. Skip Abstract Factory until you truly build families of related objects together.

**Relation to DIP:** Callers depend on the product interface. The factory (or composition root) is where concrete types are chosen. That is the wiring **[[Dependency Inversion Principle]]** expects at the edge.

## Details

### Variants

| Variant | Use when |
|---------|----------|
| Simple factory | One function or module picks the concrete type; no inheritance tree |
| Factory Method | Subclasses override which product type to instantiate |
| Abstract Factory | Clients need coordinated sets of products (UI kits, DB dialect families) |

### Implementation Notes

- Keep factories at the **composition root** (main, DI module, test setup), not deep in domain logic
- Prefer constructor injection of the product interface; factory produces the instance once at startup
- In Go, package-level `New` functions and small constructor tables are idiomatic simple factories
- Name factories after what they create (`UserRepositoryFactory`), not abstract enterprise jargon

### Common Failure Modes

- Abstract Factory for a single product with no family relationship
- Factory interface with one implementation forever (use a function instead)
- God factory that knows every subsystem in the application
- Leaking concrete product types through the factory return type

### Related Garden Items

- **[[Dependency Inversion Principle]]** for why creation should sit behind abstractions
- **[[Open-Closed Principle]]** for adding product types without editing callers
- **[[Object-Oriented Programming]]** for the paradigm where Factory Method and Abstract Factory are most common
