---
title: Stable Abstractions Principle
date: '2026-06-25'
lastmod: '2026-06-26'
draft: false
keywords:
- Stable Abstractions Principle
- SAP
params:
  aliases:
  - SAP
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - software-architecture
---

[Stable Abstractions Principle](https://en.wikipedia.org/wiki/Stable_abstractions_principle)

The [Stable Abstractions Principle](https://en.wikipedia.org/wiki/Stable_abstractions_principle) (SAP) says a component should be as abstract as it is stable. Stable packages expose interfaces and abstract types; volatile packages hold concrete implementations. We **adopt** it when widely depended-on modules are concrete classes that resist extension without edits. SAP bridges **[[Stable Dependencies Principle]]** and **[[Dependency Inversion Principle]]** at component granularity.

## Blurb

> A component should be as abstract as it is stable.

## Summary

**What it is:** A coupling rule for components. Stability (many dependents, few dependencies) should correlate with abstraction (interfaces, abstract classes, ports). Instability should correlate with concrete code that can change freely. Abstraction can be measured as the ratio of interfaces to total types.

**Why it matters:** A stable but concrete package is hard to extend without modifying source. Every new behavior risks breaking all dependents. Martin calls that profile the "zone of pain."

**Source:** Martin states the rule in *Clean Architecture* as "a component should be as abstract as it is stable."

**When to use:** Platform API design, shared kernel reviews, and refactors where a popular library is mostly concrete classes. Apply when stable modules resist **[[Open-Closed Principle]]** extension.

**When to pull back:** Small apps with no shared kernel. Do not abstract stable modules before a second implementation or test seam appears.

**Relation to siblings:** **[[Stable Dependencies Principle]]** sets dependency direction. SAP shapes what stable modules contain. **[[Acyclic Dependencies Principle]]** keeps the graph acyclic while you refactor toward abstraction at the stable core.

## Details

### Abstraction Metric

**Abstraction** (A) for a package:

`A = N_i / (N_i + N_c)`

Where **N_i** is the count of interfaces (and abstract types) and **N_c** is the count of concrete classes. **A** ranges from 0 (fully concrete) to 1 (fully abstract). SAP expects stable packages to score higher on **A**.

### Stability vs Abstraction Quadrants

| Profile | Risk |
|---------|------|
| Stable + concrete | Zone of pain: hard to change, many dependents hurt |
| Stable + abstract | Target: extend via new implementations |
| Unstable + abstract | Zone of uselessness: abstractions nobody uses |
| Unstable + concrete | Normal for feature and adapter code at the leaves |

### Component Coupling Context

SAP is one of three classic **component coupling** principles (Robert C. Martin). Siblings are **[[Acyclic Dependencies Principle]]** (ADP) and **[[Stable Dependencies Principle]]** (SDP).

| Principle | Gist |
|-----------|------|
| ADP | No cycles (**[[Acyclic Dependencies Principle]]**) |
| SDP | Depend toward stability (**[[Stable Dependencies Principle]]**) |
| SAP | Stable components stay abstract |

### Practical Signs

| Signal | Likely fix |
|--------|------------|
| Shared library is concrete classes with wide import fan-in | Extract interfaces; move concretions to unstable packages |
| Subclassing stable types breaks invariants (**[[Liskov Substitution Principle]]**) | Prefer composition and ports over deep inheritance |
| Interface-only jar with no implementations | Merge with a consumer or add reference impl (avoid uselessness zone) |
| Stable API changes require editing the same file weekly | Split volatile concretions per **[[Common Closure Principle]]** |

### Common Failure Modes

- Abstract stable packages with no real extension points (speculative SAP)
- Concrete stable god modules that every team imports
- Confusing SAP with "never put code in stable packages" (stable still needs some abstraction)
- Deep inheritance hierarchies in stable layers instead of small interfaces

### Related Garden Items

- **[[Dependency Inversion Principle]]** and **[[Open-Closed Principle]]** for class-level abstraction discipline
- **[[Stable Dependencies Principle]]** for keeping volatile code from anchoring the graph
- **[[Liskov Substitution Principle]]** when stable abstractions use inheritance
- **[[Acyclic Dependencies Principle]]** when abstraction moves require new package edges
