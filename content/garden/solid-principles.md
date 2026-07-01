---
title: SOLID Principles
date: '2026-06-24'
lastmod: '2026-06-24'
draft: false
keywords:
- SOLID Principles
- SOLID
- SOLID Pinciples
params:
  aliases:
  - SOLID
  - SOLID Pinciples
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: New
    subcategories:
    - software-architecture
---

[SOLID](https://en.wikipedia.org/wiki/SOLID) is a mnemonic for five object-oriented design principles from Robert C. Martin. Together they reduce coupling, clarify change boundaries, and keep modules testable. We **adopt** the set as baseline discipline in application code, not as a checklist to apply in one refactor. Start with **[[Single Responsibility Principle]]** and **[[Dependency Inversion Principle]]** where coupling hurts tests or vendor swaps.

## Blurb

> SOLID is a mnemonic acronym for five design principles intended to make software designs more understandable, flexible, and maintainable.

## Summary

**What it is:** Five named principles (below) that guide how classes, modules, and services depend on each other. They complement **[[Object-Oriented Programming]]** but apply at any granularity where you define boundaries and interfaces.

**Garden stance:** **Adopt** as a review vocabulary and refactoring target. **Hold** SOLID-by-the-book layers that add abstraction without a measured pain point (no second implementation, no test seam, no churn).

| Letter | Principle             | Garden item                                         |
| ------ | --------------------- | --------------------------------------------------- |
| **S**  | Single Responsibility | **[[Single Responsibility Principle]]** (**adopt**) |
| **O**  | Open/Closed           | **[[Open-Closed Principle]]** (**adopt**)           |
| **L**  | Liskov Substitution   | **[[Liskov Substitution Principle]]** (**adopt**)   |
| **I**  | Interface Segregation | **[[Interface Segregation Principle]]** (**adopt**) |
| **D**  | Dependency Inversion  | **[[Dependency Inversion Principle]]** (**adopt**)            |

**When to use:** Design review, legacy refactors, and new services where frameworks or databases would otherwise leak into domain logic. Pair with **[[First Principles]]** when inherited structure no longer fits constraints.

**When to pull back:** Scripts, glue code, and prototypes with one concrete dependency and no reuse plan.

## Details

### The Five Principles (Short Form)

| Principle | One-line gist |
|-----------|----------------|
| Single Responsibility | One reason to change per module |
| Open/Closed | Open for extension, closed for modification |
| Liskov Substitution | Subtypes must honor the base contract |
| Interface Segregation | Many small interfaces beat one fat interface |
| Dependency Inversion | Depend on abstractions, not concretions |

### Application Order (Practical)

1. **SRP** first: split mixed concerns so each unit has a clear job.
2. **DIP** next: introduce ports where tests or vendors force seams.
3. **OCP / LSP / ISP** when extension points, inheritance, or interface bloat show up in review.

### Common Failure Modes

- Renaming a god class without splitting responsibilities (SRP violation remains)
- Interface-per-class with no consumer need (fake DIP)
- Subclasses that weaken preconditions or strengthen postconditions (LSP violation)
- "SOLID refactor" that delays delivery without a coupling metric

### Related Garden Items

- **[[Single Responsibility Principle]]**, **[[Open-Closed Principle]]**, **[[Liskov Substitution Principle]]**, **[[Interface Segregation Principle]]**, and **[[Dependency Inversion Principle]]** for per-principle guidance
- **[[Design Pattern]]** for named solutions after structure is clear
- **[[Unit Testing]]** as a forcing function for inversion and narrow modules
