---
title: Common Closure Principle
date: '2026-06-24'
lastmod: '2026-07-02'
draft: false
keywords:
- Common Closure Principle
- CCP
params:
  aliases:
  - CCP
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - software-architecture
---

[Common Closure Principle](https://en.wikipedia.org/wiki/Common_closure_principle) is a technique we **adopt** in the garden.

## Summary

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

### Component Cohesion Context

CCP is one of three classic **component cohesion** principles (Robert C. Martin). Siblings are **[[Reuse-Release Equivalence Principle]]** (REP) and **[[Common Reuse Principle]]** (CRP). Teams often trade them off: tight CCP reduces release coupling; tight CRP favors convenience imports.

| Principle | Gist |
|-----------|------|
| REP | Release components as a unit when reused (**[[Reuse-Release Equivalence Principle]]**) |
| CCP | Group classes that change together |
| CRP | Group classes reused together (**[[Common Reuse Principle]]**) |

### SRP and OCP at Component Level

| Class-level principle | Component-level counterpart |
|-----------------------|----------------------------|
| **[[Single Responsibility Principle]]** (one reason to change) | CCP (one change driver per component) |
| **[[Open-Closed Principle]]** (closed to unrelated change) | CCP splits (unrelated concerns in separate deployables) |

### Practical Signs

| Signal | Likely fix |
|--------|------------|
| Unrelated teams block on one library version | Split by change axis (CCP) |
| Frequent releases touch files that never co-change | Move outliers to another package |
| "Kitchen sink" shared module | Peel off domains with different owners |

### Common Failure Modes

- `common` or `utils` packages that accumulate every cross-cutting helper
- Microservices split by technical layer (all SQL in one service) instead of change driver
- Monorepo packages named by org chart that do not match deploy or change patterns
- Confusing CCP with "put everything in one repo" (version and release boundaries still matter)

### Related Garden Items

- **[[Single Responsibility Principle]]** for class-level one-reason-to-change discipline
- **[[SOLID Principles]]** for in-component class design after boundaries are drawn
- **[[Open-Closed Principle]]** for extension without unrelated modification at class level
- **[[Common Reuse Principle]]** and **[[Reuse-Release Equivalence Principle]]** for the other cohesion principles
- **[[Acyclic Dependencies Principle]]**, **[[Stable Dependencies Principle]]**, and **[[Stable Abstractions Principle]]** for component coupling
- **[[Dependency Inversion Principle]]** for stable ports across component seams
