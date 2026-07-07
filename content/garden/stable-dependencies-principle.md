---
title: Stable Dependencies Principle
date: '2026-06-25'
lastmod: '2026-07-02'
draft: false
keywords:
- Stable Dependencies Principle
- SDP
params:
  aliases:
  - SDP
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - software-architecture
---

[Stable Dependencies Principle](https://en.wikipedia.org/wiki/Stable_dependencies_principle) is a technique we **adopt** in the garden.

## Summary

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

### Stability Metrics

Martin uses fan-in and fan-out at the package level. High fan-in (many importers) increases stability because many teams feel each change. High fan-out (many imports) increases instability.

**Instability** (I) for a package:

`I = Ce / (Ca + Ce)`

Where **Ce** is efferent coupling (outgoing dependencies) and **Ca** is afferent coupling (incoming dependents). **I** ranges from 0 (maximally stable) to 1 (maximally unstable). SDP means edges should point from higher **I** toward lower **I**.

| Package profile | Typical role |
|---------------|--------------|
| High fan-in, low fan-out | Stable foundation (types, ports, policy) |
| Low fan-in, high fan-out | Volatile leaf (features, adapters, experiments) |
| Stable depending on unstable | SDP violation; invert or relocate code |

### Component Coupling Context

SDP is one of three classic **component coupling** principles (Robert C. Martin). Siblings are **[[Acyclic Dependencies Principle]]** (ADP) and **[[Stable Abstractions Principle]]** (SAP).

| Principle | Gist |
|-----------|------|
| ADP | No cycles (**[[Acyclic Dependencies Principle]]**) |
| SDP | Depend toward stability |
| SAP | Stable means abstract (**[[Stable Abstractions Principle]]**) |

### Practical Signs

| Signal | Likely fix |
|--------|------------|
| Shared `kernel` imports feature flags from `webapp` | Move flags behind a port; invert dependency |
| Platform library release blocked by one product team | Peel product-specific code out of the library |
| "Utils" package grows because everything imports it | Check whether utils became an unstable dumping ground |
| Frequent breaks in widely used internal SDK | SDP review plus **[[Common Closure Principle]]** split |

### Common Failure Modes

- Treating "stable" as "old" instead of measuring fan-in and fan-out
- Inverting dependencies with empty interfaces (fake stability)
- Freezing the wrong layer because it has a good name (`core`, `common`)
- Ignoring SDP while enforcing folder-based layer rules that code bypasses

### Related Garden Items

- **[[Dependency Inversion Principle]]** for abstraction seams that fix inverted dependencies
- **[[Stable Abstractions Principle]]** for keeping stable packages extensible
- **[[Acyclic Dependencies Principle]]** as the first check on the same graph
- **[[Common Closure Principle]]** for grouping volatile code so it stays at the leaves
