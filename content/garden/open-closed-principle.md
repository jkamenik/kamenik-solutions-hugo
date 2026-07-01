---
title: Open-Closed Principle
date: '2026-06-24'
lastmod: '2026-06-24'
draft: false
keywords:
- Open-Closed Principle
- OCP
- Open/Closed Principle
- Open-Close Principle
params:
  aliases:
  - OCP
  - Open/Closed Principle
  - Open-Close Principle
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: New
    subcategories:
    - software-architecture
---

[Open-Closed Principle](https://en.wikipedia.org/wiki/Open%E2%80%93closed_principle)

The [Open-Closed Principle](https://en.wikipedia.org/wiki/Open%E2%80%93closed_principle) (OCP) says software entities should be open for extension but closed for modification. We **adopt** it when new behavior arrives often but existing code is stable and well tested. Add extension points (interfaces, plugins, strategy objects) instead of editing core logic each time. It is the **O** in **[[SOLID Principles]]**.

## Blurb

> Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification.

## Summary

**What it is:** A stability rule. You extend behavior by adding new code (subtypes, plugins, handlers) rather than changing working implementations. Callers depend on abstractions that new variants plug into.

**Why it matters:** Every edit to shared core code risks regressions across the system. OCP localizes change to new types or modules and keeps proven paths untouched.

**When to use:** Pricing rules, notification channels, auth providers, export formats, and policy engines where product adds variants regularly. Natural fit with **[[Design Pattern]]** choices like Strategy, Template Method, and Decorator.

**When to pull back:** Code with one implementation and no forecast of variation. Do not add plugin frameworks before a second behavior exists. YAGNI still applies.

**Relation to siblings:** **[[Single Responsibility Principle]]** narrows units first. **[[Dependency Inversion Principle]]** supplies the abstractions OCP extends. Apply OCP after you can name the variation axis.

## Details

### Extension Mechanisms

| Mechanism | Fit |
|-----------|-----|
| Interface + new implementation | Swappable backends (storage, payment) |
| Registry of handlers | Event types, CLI subcommands |
| Configuration-driven behavior | Feature flags, rule tables |
| Subclassing | Use sparingly; favor composition |

### Common Failure Modes

- Abstract factories before a second concrete type exists
- Deep inheritance trees where each new feature edits a base class
- "Closed" code that is actually frozen because nobody dares to touch it
- Plugin systems with no isolation (extensions break the core)

### Practical Checklist

1. Name the axis of change (what varies vs what stays stable).
2. Introduce an abstraction callers already need for **[[Dependency Inversion Principle]]**.
3. Add the new behavior as a new type or module, not a branch in the old one.
4. Keep extension points small; fat interfaces violate **[[Interface Segregation Principle]]**.

### Related Garden Items

- **[[SOLID Principles]]** for the full mnemonic and sibling principles
- **[[Design Pattern]]** for Strategy, Decorator, and Template Method after the extension point is clear
- **[[Object-Oriented Programming]]** for the paradigm OCP most often applies to
