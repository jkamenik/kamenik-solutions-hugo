---
title: Factory Pattern
date: '2026-06-24'
lastmod: '2026-07-02'
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
    movement: No Change
    subcategories:
    - design-pattern
---

[Factory Pattern](https://en.wikipedia.org/wiki/Factory_method_pattern). The [Factory pattern](https://en.wikipedia.org/wiki/Factory_method_pattern) family centralizes object creation behind an interface or function so callers depend on abstractions, not concrete constructors.

## Summary

**Garden stance:** We **adopt** Factory Pattern for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

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
