---
title: Stable Dependencies Principle
date: '2026-06-25'
lastmod: '2026-06-26'
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

[Stable Dependencies Principle](https://en.wikipedia.org/wiki/Stable_dependencies_principle)

The [Stable Dependencies Principle](https://en.wikipedia.org/wiki/Stable_dependencies_principle) (SDP) says dependencies should point toward stability. A volatile module may depend on a stable one, not the reverse. We **adopt** it when frequent feature work destabilizes core libraries because low-level packages import high-churn UI or experiment code. It extends **[[Dependency Inversion Principle]]** from classes to components and pairs with **[[Acyclic Dependencies Principle]]** on the same dependency graph.

## Blurb

> Depend in the direction of stability.

## Summary

**What it is:** A coupling rule for components. Stability means hard to change: many dependents (high fan-in), few outgoing dependencies (low fan-out). Instability is the opposite. SDP forbids stable packages from depending on unstable ones. Stability and instability can be measured from dependency counts.

**Why it matters:** When stable core modules depend on volatile leaf code, every experiment ripples through the foundation. Teams fear changing shared libraries because unknown consumers break.

**Source:** Martin states the rule in *Clean Architecture* as "depend in the direction of stability."

**When to use:** Library layering reviews, platform versus product boundary debates, and refactors where `core` imports from `app`. Apply when dependency metrics or import graphs show inverted stability.

**When to pull back:** Early single-team codebases with one deployable. Do not freeze layers before you know which modules are truly shared and long-lived.

**Relation to siblings:** **[[Stable Abstractions Principle]]** (SAP) adds that stable modules should stay abstract. **[[Acyclic Dependencies Principle]]** ensures the graph has no cycles before stability direction matters.

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
