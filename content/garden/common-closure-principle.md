---
title: Common Closure Principle
date: '2026-06-24'
lastmod: '2026-06-26'
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

[Common Closure Principle](https://en.wikipedia.org/wiki/Common_closure_principle)

The [Common Closure Principle](https://en.wikipedia.org/wiki/Common_closure_principle) (CCP) groups classes into the same component when they change for the same reasons and at the same times. We **adopt** it at package, module, and service boundaries where deploy units should match change drivers. It is the component-level counterpart to **[[Single Responsibility Principle]]**. Keep unrelated change axes in separate deployables so a tweak in billing does not force a release of search.

## Blurb

> Gather into components those classes that are likely to change for the same reasons and at the same times. Separate into different components those classes that change at different times and for different reasons.

## Summary

**What it is:** A cohesion rule for components (packages, modules, libraries, microservices). Everything in one deploy unit should share a change lifecycle. If two classes rarely change together, they should not live in the same component.

**Why it matters:** Violations inflate release blast radius. A one-line fix in shared utilities rebuilds and redeploys unrelated services. Teams wait on each other because unrelated concerns share a version line.

**When to use:** Monorepo package splits, library boundaries, and microservice cuts. Apply when you can name distinct stakeholders or business reasons that drive change (billing vs catalog vs auth).

**When to pull back:** Early prototypes and single-team apps where one deployable is fine. Do not split packages before you see divergent change rates in practice.

**Relation to SRP:** **[[Single Responsibility Principle]]** applies at class and function granularity. CCP applies the same idea one level up: one reason to change per component, not only per class. A component with multiple change drivers violates CCP the way a god class violates SRP.

**Relation to OCP:** **[[Open-Closed Principle]]** says modules should be open for extension but closed to unrelated modification. CCP keeps unrelated change axes in separate components so a billing tweak does not force a search release.

**Source:** Martin states the rule in *Clean Architecture* as "gather into components those classes that change for the same reason."

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
