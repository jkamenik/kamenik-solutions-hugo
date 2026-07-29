---
title: BDD
date: '2026-07-29'
lastmod: '2026-07-29'
draft: false
keywords:
- BDD
- Behavior-Driven Development
- Behaviour-Driven Development
params:
  aliases:
  - Behavior-Driven Development
  - Behaviour-Driven Development
  garden:
    kind: item
    usefulness: hold
    category: technique
    movement: No Change
---

[Behaviour-driven development (BDD)](https://dannorth.net/blog/introducing-bdd/) extends **[[TDD]]** so tests describe desired behavior in plaintext. We **hold** it for new process design: **[[Spec-Driven Development (SDD)]]** replaces it by putting the agent inside the specification.

## Blurb

> Behaviour-driven development (BDD) has evolved out of established agile practices and is designed to make them more accessible and effective for teams new to agile software delivery.

## Summary

**What it is:** Dan North's evolution of **[[TDD]]**: name behaviors in sentences, prioritize valuable missing behavior, and capture acceptance as readable scenarios (often Given/When/Then).

**Lineage:** **[[TDD]]** → BDD (plain-text behavior) → **[[Spec-Driven Development (SDD)]]** (spec includes agent). Do not start new work as BDD-only. Fold BDD's plain-text behaviors and acceptance scenarios into the SDD specification.

**When to use (existing only):**

| Situation | Notes |
|-----------|--------|
| Inherited scenario suites | Keep if maintained; migrate process toward SDD |
| Teaching history | Explain behavior language as the bridge from TDD to SDD |

**When to skip (new work):**

- Greenfield delivery process: use **[[Spec-Driven Development (SDD)]]**
- Agent-assisted multi-file work needs a reviewed spec that includes the agent, not Gherkin theater alone

**Trade-offs:** BDD fixed TDD's "test" vocabulary and shared language. SDD absorbs that plain-text behavior requirement and adds the agent as a first-class part of the spec.

## Details

Useful BDD habits that SDD specs should still include:

- Behavior described in plain sentences (not jargon-only tests)
- Next most important missing behavior
- Scenarios: Given context, When event, Then outcomes

**References**

- [Dan North: Introducing BDD](https://dannorth.net/blog/introducing-bdd/)
- [Dan North: BDD is like TDD if…](https://dannorth.net/blog/bdd-is-like-tdd-if/)
