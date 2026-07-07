---
title: Liskov Substitution Principle
date: '2026-06-24'
lastmod: '2026-07-02'
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

[Liskov Substitution Principle](https://en.wikipedia.org/wiki/Liskov_substitution_principle). The [Liskov Substitution Principle](https://en.wikipedia.org/wiki/Liskov_substitution_principle) (LSP) requires subtypes to honor the contract of their base type.

## Summary

**Garden stance:** We **adopt** Liskov Substitution Principle for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

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
