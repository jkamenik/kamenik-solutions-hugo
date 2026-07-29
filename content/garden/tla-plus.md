---
title: TLA+
date: '2026-07-23'
lastmod: '2026-07-29'
draft: false
keywords:
- TLA+
- TLA Plus
- Temporal Logic of Actions
params:
  aliases:
  - TLA Plus
  - Temporal Logic of Actions
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: No Change
    subcategories:
    - specification
---

[TLA+](https://lamport.azurewebsites.net/tla/tla.html) is Leslie Lamport's formal language for modeling concurrent and distributed systems with mathematics. We **assess** it when control loops or protocols are small enough to specify, and design bugs would be expensive in code.

## Blurb

> TLA+ is a language for writing and checking “specifications”, or system designs. Once you have your specification, you can then test the specification directly for bugs, even before you’ve written any code.

## Summary

**What it is:** Spec language based on set theory, first-order logic, and the Temporal Logic of Actions. Typical form is `Init ∧ □Next ∧ Liveness`. Checked with TLC (model checker) and TLAPS (proof system). Industry use at AWS, Microsoft, and others for protocol design.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Small orchestration surfaces | Reconcilers, consensus, failover with few CRDs or state machines |
| Safety and liveness proofs | Exhaustive check of interleavings humans miss |
| Agent-driven infra | Specs become harnesses agents and CI can re-run on every change |

**When to skip:**

- Specs larger than the implementation (wrong abstraction level)
- Teams unwilling to learn math-style modeling
- Code already covered by property tests alone with no concurrent design risk

**Trade-offs:** Catches design errors before code. Steep learning curve. Best paired with **[[PlusCal]]** for algorithm-shaped models, then raw TLA+ for refinement and fairness.

## Details

### Tools

| Tool | Role |
|------|------|
| TLC | Explicit-state model checker |
| TLAPS | Machine-checked proofs |
| TLA Toolbox / VS Code extension | IDE for specs and tools |

### Fit With Small Surfaces

TLA+ pays off when the orchestration surface is small enough to model. Examples: a few custom resources, a short state machine, or a consensus protocol. Pair TLC with property tests in the implementation language so the same invariants show up in CI.

Works well next to **[[Modular Monolith]]** designs and **[[Kubernetes]]** controllers whose reconcile loops stay finite and explicit.

### Related Garden Items

- **[[PlusCal]]** - imperative algorithm language that translates to TLA+
- **[[Specification]]** - subcategory for external specs and formal models
- **[[Modular Monolith]]** - architectures small enough to verify

### References

- [Leslie Lamport TLA+ home](https://lamport.azurewebsites.net/tla/tla.html)
- [Learn TLA+ FAQ](https://www.learntla.com/intro/faq.html) (Blurb source)
- [TLA+ community / tlapl.us](https://www.tlapl.us/) (currently Lamport's personal site; Foundation transition noted there)
