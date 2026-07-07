---
title: Single Responsibility Principle
date: '2025-05-13'
lastmod: '2026-07-02'
draft: false
keywords:
- Single Responsibility Principle
- SRP
params:
  aliases:
  - SRP
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - software-architecture
---

[Single Responsibility Principle](https://en.wikipedia.org/wiki/Single-responsibility_principle) is a technique we **adopt** in the garden.

## Summary

**What it is:** A coupling rule. Each unit of code owns a single concern. A data transformer should not also handle I/O. A config parser should not also validate business rules.

**Why it matters:** SRP is not about making things small for its own sake. When code changes for two different reasons, those reasons eventually conflict. Every change risks breaking the other concern.

**When to use:** Functions, classes, services, and microservice boundaries wherever reviewers can name two unrelated change drivers. Foundational for maintainable, testable code.

**When to pull back:** Do not split a cohesive algorithm into artificial micro-functions with no reuse. Size is a side effect; separation of reasons is the goal.

**Signs of violation:** Functions with "and" in the name, classes with unrelated method clusters, modules that import from two unrelated domains. The fix is usually extract: move the second concern behind a clear interface.

## Details

### Granularity

| Level | Example split |
|-------|----------------|
| Function | Parse config vs validate business rules |
| Class | Repository vs HTTP handler |
| Service | Billing vs notifications |
| Microservice | One bounded context per deployable unit |

### Common Failure Modes

- God classes that accumulate every feature touching one noun
- Premature extraction that fragments a single algorithm
- "Single responsibility" used to justify one-method classes with no cohesion
- Splitting by technical layer only (all SQL in one giant module)

### Application Order

1. Apply SRP first when refactoring tangled modules.
2. Introduce **[[Dependency Inversion Principle]]** after responsibilities are narrow enough to define ports.
3. Name **[[Design Pattern]]** choices only after the split surfaces a real extension point.

### Related Garden Items

- **[[SOLID Principles]]** for the full mnemonic and sibling principles
- **[[Object-Oriented Programming]]** for the paradigm SRP most often supports
- **[[Unit Testing]]** as a forcing function for narrow, mockable units
