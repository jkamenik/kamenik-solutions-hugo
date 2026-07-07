---
title: Acyclic Dependencies Principle
date: '2026-06-25'
lastmod: '2026-07-02'
draft: false
keywords:
- Acyclic Dependencies Principle
- ADP
params:
  aliases:
  - ADP
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - software-architecture
---

[Acyclic Dependencies Principle](https://en.wikipedia.org/wiki/Acyclic_dependencies_principle) is a technique we **adopt** in the garden.

## Summary

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

### Component Coupling Context

ADP is one of three classic **component coupling** principles (Robert C. Martin). Siblings are **[[Stable Dependencies Principle]]** (SDP) and **[[Stable Abstractions Principle]]** (SAP).

| Principle | Gist |
|-----------|------|
| ADP | No cycles in the component graph |
| SDP | Depend toward more stable components (**[[Stable Dependencies Principle]]**) |
| SAP | Stable components stay abstract (**[[Stable Abstractions Principle]]**) |

### Breaking Cycles (Practical)

| Technique | When it fits |
|-----------|--------------|
| Extract shared interface to a third package | Two modules need each other's types |
| **[[Dependency Inversion Principle]]** (preferred) | High-level module should not depend on low-level detail; extract shared interface |
| Event or message boundary | Runtime decoupling when compile-time inversion is awkward |
| Merge components | Cycle means the split was wrong; reunify |

### Practical Signs

| Signal | Likely fix |
|--------|------------|
| Build order only works with hacks or `--force` | Map imports; break the smallest back-edge |
| `common` imports from `features` and vice versa | Invert dependency or extract shared kernel |
| Microservices call each other synchronously in a ring | Introduce events or consolidate ownership |
| Refactor blocked because "everything depends on everything" | ADP review before more features |

### Common Failure Modes

- Ignoring test-only or devDependency cycles that mirror production cycles
- Breaking a cycle by moving code to a junk-drawer `shared` package (creates a god module)
- Layer rules on paper while code imports whatever is convenient
- Splitting services without removing synchronous call loops

### Related Garden Items

- **[[Stable Dependencies Principle]]** and **[[Stable Abstractions Principle]]** for direction of dependencies after the graph is acyclic
- **[[Dependency Inversion Principle]]** for introducing abstractions at cycle breaks
- **[[Reuse-Release Equivalence Principle]]** for versioned components that ADP keeps independently releasable
