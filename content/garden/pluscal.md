---
title: PlusCal
date: '2026-07-23'
lastmod: '2026-07-23'
draft: false
keywords:
- PlusCal
- PlusCal algorithm language
- P-Cal
params:
  aliases:
  - PlusCal algorithm language
  - P-Cal
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: No Change
    subcategories:
    - specification
---

[PlusCal](https://lamport.azurewebsites.net/pubs/pluscal.pdf) is Leslie Lamport's algorithm language for verifiable pseudocode that translates into **[[TLA+]]**. We **assess** it for complex workflows whose state transitions and invariants are precise enough to model.

## Blurb

> PlusCal is an algorithm language that can be used right now to replace pseudo-code, for both sequential and concurrent algorithms. It is based on the TLA+ specification language, and a PlusCal algorithm is automatically translated to a TLA+ specification that can be checked with the TLC model checker and reasoned about formally.

## Summary

**What it is:** A formally defined, imperative-style algorithm language with verbose P-syntax and compact C-syntax. The TLA+ Toolbox translates PlusCal into a specification that TLC can explore across possible states and interleavings.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Finite state machines | State transitions are explicit, but invocation paths are complex |
| Kubernetes operators | Reconcile loops, retries, stale reads, and partial failures create interleavings |
| Durable execution | Multi-step workflows need invariants across retries, crashes, and recovery |
| Teaching or onboarding | Algorithm syntax is often easier to approach than raw **[[TLA+]]** |

**When to skip:**

- The system cannot be reduced to bounded state and meaningful invariants
- The specification is already a mathematical relation rather than an algorithm
- Refinement or fairness needs require raw **[[TLA+]]**
- The team expects a drop-in **[[Test Framework]]** or native test generator

**Testing role:** PlusCal checks a model, not the implementation. TLC produces explored behaviors, simulation traces, and counterexamples. A separate adapter must translate selected traces and invariants into tests for the implementation language.

**Trade-offs:** PlusCal makes algorithm-shaped specifications approachable. The translation must stay synchronized, and the model can diverge from production code. Pair model checking with implementation-level property and integration tests.

## Details

### Relationship to **[[TLA+]]**

| Layer | Role |
|-------|------|
| PlusCal | Write labeled processes, actions, and state changes |
| Translator | Emit TLA+ `Init`, `Next`, and control-state definitions |
| TLC | Explore reachable states, check invariants, and produce traces |
| Raw TLA+ | Express refinement, advanced fairness, and proofs beyond PlusCal |
| Native tests | Exercise the implementation through a project-specific adapter |

### From Model to Native Tests

1. Model operations, state, failure points, and invariants in PlusCal.
2. Translate to **[[TLA+]]** and check bounded models with TLC.
3. Save representative simulation traces and counterexample traces.
4. Map model actions and state values to the system's public API.
5. Replay selected traces through a language-specific test adapter.
6. Assert the same invariants against implementation state and outputs.

TLC can generate or display traces, but PlusCal does not directly emit native test code. The adapter and trace-selection policy are project work. Start with counterexamples and high-risk interleavings rather than attempting to replay the full state graph.

### Fit With Control Loops

PlusCal fits labeled steps, processes, and shared state. A useful pattern models a reconcile loop, checks it with TLC, then mirrors the invariants in tests against **[[Kubernetes]]** controllers or **[[Modular Monolith]]** orchestration.

### References

- Leslie Lamport, [The PlusCal Algorithm Language (PDF)](https://lamport.azurewebsites.net/pubs/pluscal.pdf)
- [PlusCal tutorial: examining TLC error traces](https://lamport.azurewebsites.net/tla/tutorial/session3.html)
- [P-syntax manual (PDF)](https://lamport.azurewebsites.net/tla/p-manual.pdf)
- Parent technique: **[[TLA+]]**
