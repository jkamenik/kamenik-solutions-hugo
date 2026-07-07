---
title: Common Reuse Principle
date: '2026-06-24'
lastmod: '2026-07-02'
draft: false
keywords:
- Common Reuse Principle
- CRP
params:
  aliases:
  - CRP
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - software-architecture
---

[Common Reuse Principle](https://en.wikipedia.org/wiki/Common_reuse_principle) is a technique we **adopt** in the garden.

## Summary

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

### Component Cohesion Context

CRP is one of three classic **component cohesion** principles (Robert C. Martin). Siblings are **[[Reuse-Release Equivalence Principle]]** (REP) and **[[Common Closure Principle]]** (CCP).

| Principle | Gist |
|-----------|------|
| REP | Release components as a unit when reused (**[[Reuse-Release Equivalence Principle]]**) |
| CCP | Group classes that change together (**[[Common Closure Principle]]**) |
| CRP | Group classes reused together |

Martin notes you cannot maximize all three at once. Tight CRP favors smaller, use-aligned bundles. Tight CCP favors independent release by change axis. Pick the pain you are solving.

### ISP at Component Level

| Level | Principle | Rule |
|-------|-----------|------|
| Type / interface | **[[Interface Segregation Principle]]** | Do not depend on methods you do not use |
| Package / module | CRP | Do not depend on classes you do not use |

### Practical Signs

| Signal | Likely fix |
|--------|------------|
| Consumer imports one helper from a large `common` package | Split by client use case (CRP) |
| Dependency graph shows disjoint class clusters in one module | Extract sub-packages |
| Security or license review flags unused transitive deps | Peel unused classes into separate artifacts |
| Every consumer rebuilds when one rarely used class changes | Consider **[[Common Closure Principle]]** split instead |

### Common Failure Modes

- Kitchen-sink `utils` or `common` packages everyone depends on
- Bundling unrelated DTOs because they share a folder
- Splitting so fine that consumers juggle dozens of tiny modules
- Optimizing CRP while ignoring divergent change rates (CCP conflict)

### Related Garden Items

- **[[Interface Segregation Principle]]** for method-level "depend only on what you use"
- **[[Common Closure Principle]]** and **[[Reuse-Release Equivalence Principle]]** for the other cohesion principles
- **[[Acyclic Dependencies Principle]]**, **[[Stable Dependencies Principle]]**, and **[[Stable Abstractions Principle]]** for component coupling
- **[[Single Responsibility Principle]]** for class-level narrowing before package splits
