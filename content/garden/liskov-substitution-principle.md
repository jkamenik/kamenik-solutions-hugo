---
title: Liskov Substitution Principle
date: '2026-06-24'
lastmod: '2026-06-24'
draft: false
keywords:
- Liskov Substitution Principle
- LSP
- Liskov Substitution
params:
  aliases:
  - LSP
  - Liskov Substitution
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - software-architecture
---

[Liskov Substitution Principle](https://en.wikipedia.org/wiki/Liskov_substitution_principle)

The [Liskov Substitution Principle](https://en.wikipedia.org/wiki/Liskov_substitution_principle) (LSP) requires subtypes to honor the contract of their base type. Callers should not need to know which concrete subtype they hold. We **adopt** it wherever polymorphism, inheritance, or interface implementations are in play. Violations surface as surprise exceptions, broken invariants, or `instanceof` checks in calling code. It is the **L** in **[[SOLID Principles]]**.

## Blurb

> Subtype objects should be substitutable for their supertype objects without altering the correctness of the program.

## Summary

**What it is:** A behavioral contract rule. If code works with a base type, swapping in any subtype must preserve expectations (inputs, outputs, errors, and invariants). Inheritance and implementation are not just syntax. They are promises to callers.

**Why it matters:** Broken substitutability forces callers to branch on concrete types. That undoes **[[Open-Closed Principle]]** and **[[Dependency Inversion Principle]]**. Tests pass on the parent mock but fail in production on a subclass.

**When to use:** Class hierarchies, interface implementations, and plugin registries where callers depend on abstractions. Review any `extends` or `implements` during design and code review.

**When to pull back:** Favor composition over inheritance when the subtype relationship is awkward. A has-a wrapper often beats a forced is-a hierarchy.

**Relation to siblings:** **[[Open-Closed Principle]]** adds subtypes for new behavior. LSP ensures those subtypes are safe to plug in. **[[Dependency Inversion Principle]]** depends on LSP holding at runtime, not only at compile time.

## Details

### Contract Checklist

| Expectation | Violation signal |
|-------------|------------------|
| Preconditions | Subtype requires stricter inputs than the base |
| Postconditions | Subtype returns weaker guarantees |
| Invariants | Subtype breaks rules the base always maintained |
| Exceptions | Subtype throws errors callers did not expect |
| Behavior | Subtype ignores or no-ops base operations |

### Classic Examples

- **Square/rectangle:** A square subtype of rectangle that breaks independent width/height setters
- **Read-only collection:** A subtype that throws on `add` when the base promised mutability
- **Null returns:** A subtype that returns null where the base never did

### Safer Alternatives

- Prefer composition and small interfaces over deep inheritance
- Use **[[Design Pattern]]** Strategy or Adapter when behavior varies without an is-a relationship
- Keep base contracts explicit in tests (contract tests for each implementation)

### Common Failure Modes

- Subclassing for reuse only (inherits API the child cannot honor)
- Empty overrides that silently disable base behavior
- `instanceof` or type switches in callers to paper over bad hierarchies
- Framework base classes that encourage override hooks with unclear contracts

### Related Garden Items

- **[[Open-Closed Principle]]** for extension without modifying stable core code
- **[[Object-Oriented Programming]]** for the paradigm where LSP applies most often
- **[[SOLID Principles]]** for the full mnemonic and remaining principles
