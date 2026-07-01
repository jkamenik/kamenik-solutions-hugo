---
title: Acyclic Dependencies Principle
date: '2026-06-25'
lastmod: '2026-06-26'
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

[Acyclic Dependencies Principle](https://en.wikipedia.org/wiki/Acyclic_dependencies_principle)

The [Acyclic Dependencies Principle](https://en.wikipedia.org/wiki/Acyclic_dependencies_principle) (ADP) forbids cycles in the component dependency graph. Package A may depend on B, but no chain of dependencies may loop back to A. We **adopt** it in monorepos, modular monoliths, and multi-service estates where circular imports block builds or force big-bang releases. Break cycles with **[[Dependency Inversion Principle]]** seams or event boundaries before layering rules fail in production.

## Blurb

> Allow no cycles in the component dependency graph.

## Summary

**What it is:** A coupling rule for components (packages, modules, libraries, deploy units). The dependency graph must be a directed acyclic graph (DAG). Cycles force mutual rebuilds and hide a clear build or release order.

**Why it matters:** Circular dependencies make incremental change expensive. A tweak in one module ripples through the cycle. Tests and deploys cannot isolate a single component. Teams co-own tangled code because ownership follows the cycle.

**Source:** Martin states the rule in *Clean Architecture* as "allow no cycles in dependencies."

**Breaking cycles:** **[[Dependency Inversion Principle]]** is the primary tool: extract an abstraction, move it to a third package, and invert the dependency so both sides depend on the interface.

**When to use:** Package dependency reviews, monorepo lint rules, and architecture checks before extract-to-library refactors. Apply when build tools or import graphs already show back-edges between modules.

**When to pull back:** Tiny single-package apps with no module boundaries. Do not invent package splits solely to satisfy a linter when there is no real component graph.

**Relation to siblings:** **[[Stable Dependencies Principle]]** and **[[Stable Abstractions Principle]]** govern how acyclic edges should point (toward stability and abstraction). ADP is the prerequisite: fix cycles first, then aim dependency direction.

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
