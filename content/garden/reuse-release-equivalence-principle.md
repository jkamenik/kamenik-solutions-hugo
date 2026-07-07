---
title: Reuse-Release Equivalence Principle
date: '2026-06-25'
lastmod: '2026-07-02'
draft: false
keywords:
- Reuse-Release Equivalence Principle
- REP
- Reuse/Release Equivalence Principle
params:
  aliases:
  - REP
  - Reuse/Release Equivalence Principle
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - software-architecture
---

[Reuse-Release Equivalence Principle](https://en.wikipedia.org/wiki/Reuse/release_equivalence_principle). The [Reuse-Release Equivalence Principle](https://en.wikipedia.org/wiki/Reuse/release_equivalence_principle) (REP) says the unit of reuse is the unit of release.

## Summary

**Garden stance:** We **adopt** Reuse-Release Equivalence Principle for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

### Component Cohesion Context

REP is one of three classic **component cohesion** principles (Robert C. Martin). Siblings are **[[Common Closure Principle]]** (CCP) and **[[Common Reuse Principle]]** (CRP). Teams cannot maximize all three at once; pick the pain you are solving.

| Principle | Gist |
|-----------|------|
| REP | Release components as a unit when reused |
| CCP | Group classes that change together (**[[Common Closure Principle]]**) |
| CRP | Group classes reused together (**[[Common Reuse Principle]]**) |

### Practical Signs

| Signal | Likely fix |
|--------|------------|
| Teams copy source files instead of depending on a package | Publish a versioned artifact (REP) |
| Shared code changes without semver or release notes | Add release process and version pins |
| Consumers on different commits of the same folder | Cut releases; document upgrade path |
| One repo folder, many implicit "versions" | Tag releases; treat the folder as one component |

### Versioning Requirement

REP is not satisfied by grouping code in a shared folder. Consumers must depend on **released, versioned artifacts** (semver tags, package registry entries, or equivalent). A release bundles a cohesive unit; consumers choose when to adopt each version.

### Common Failure Modes

- Reuse without versioning (every consumer tracks main)
- Semver on paper but breaking changes in patch releases
- One giant release train for unrelated modules (REP without CCP or CRP thought)
- Release process so heavy that teams bypass it with duplication

### Related Garden Items

- **[[Common Closure Principle]]** and **[[Common Reuse Principle]]** for the other cohesion principles
- **[[Acyclic Dependencies Principle]]**, **[[Stable Dependencies Principle]]**, and **[[Stable Abstractions Principle]]** for component coupling rules
- **[[Dependency Inversion Principle]]** for stable seams between released components
