---
title: Common Reuse Principle
date: '2026-06-24'
lastmod: '2026-06-26'
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

[Common Reuse Principle](https://en.wikipedia.org/wiki/Common_reuse_principle)

The [Common Reuse Principle](https://en.wikipedia.org/wiki/Common_reuse_principle) (CRP) groups classes into the same component when they are used together. Consumers should not depend on classes they never touch. We **adopt** it when shared libraries force unrelated transitive dependencies or version churn. CRP pushes modules toward smaller artifacts that match real use. It is the component-level counterpart to **[[Interface Segregation Principle]]**.

## Blurb

> Classes that are not used together should not be grouped together.

## Summary

**What it is:** A reuse cohesion rule for packages, modules, and libraries. If a consumer needs one class from a component, it should plausibly need the rest. Split components when clients import a jar or module but use only a slice of its surface. CRP is **[[Interface Segregation Principle]]** applied to deployable units.

**Why it matters:** Fat shared modules drag unused code, licenses, and security surface into every consumer. A change to an unrelated class in the same artifact still forces retest and redeploy downstream.

**Source:** Martin states two related rules in *Clean Architecture*: do not force users of a component to depend on things they do not need, and do not depend on things you do not need.

**When to use:** Shared internal libraries, platform SDKs, and monorepo packages where teams complain about "pulling in all of X for one helper." Apply when usage graphs show clients depending on disjoint subsets of the same module.

**When to pull back:** Small teams with one app and one deployable do not need package surgery early. Do not split until reuse patterns are visible in imports or dependency graphs.

**Relation to siblings:** **[[Interface Segregation Principle]]** keeps interfaces small at the type level. CRP keeps components small at the deploy/import level and drives modules toward smaller artifacts. **[[Common Closure Principle]]** groups by shared change; CRP groups by shared use. Teams often trade CCP against CRP.

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
