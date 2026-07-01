---
title: Reuse-Release Equivalence Principle
date: '2026-06-25'
lastmod: '2026-06-26'
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

[Reuse-Release Equivalence Principle](https://en.wikipedia.org/wiki/Reuse/release_equivalence_principle)

The [Reuse-Release Equivalence Principle](https://en.wikipedia.org/wiki/Reuse/release_equivalence_principle) (REP) says the unit of reuse is the unit of release. Anything consumers reuse must ship with version numbers, changelogs, and release discipline. We **adopt** it when shared libraries or internal packages are copied ad hoc instead of versioned artifacts. REP only works when releases are versioned and the artifact is one cohesive group. It pairs with **[[Common Closure Principle]]** and **[[Common Reuse Principle]]** as one of three component cohesion rules.

## Blurb

> The granule of reuse is the granule of release.

## Summary

**What it is:** A cohesion rule for components (packages, modules, libraries). Classes grouped for reuse must release together under a shared version line. Everything in the release artifact should belong to one cohesive group. Reusers can pin a version, read release notes, and upgrade on their schedule.

**Why it matters:** Informal reuse (copy-paste, path imports, floating HEAD) hides breaking changes. Teams cannot coordinate upgrades or roll back when a shared module shifts without notice. Without version numbers and a release process, REP is only a label.

**Source:** Martin states the rule in *Clean Architecture* as "the granule of reuse is the granule of release."

**When to use:** Internal platform libraries, shared SDKs, and monorepo packages other teams depend on. Apply when more than one consumer needs predictable versioning and release communication.

**When to pull back:** Single-app prototypes with one deployable and no external consumers. Do not add release overhead before a module has a second consumer.

**Relation to siblings:** **[[Common Closure Principle]]** groups by shared change. **[[Common Reuse Principle]]** groups by shared use. REP adds release engineering: the bundle you import is the bundle you version.

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
