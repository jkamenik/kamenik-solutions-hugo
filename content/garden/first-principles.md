---
title: "First Principles"
date: 2026-06-22
lastmod: 2026-06-22
draft: false

keywords:
  - First Principles
  - First Principles Thinking
  - Reasoning from First Principles

params:
  aliases:
    - First Principles Thinking
    - Reasoning from First Principles
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "No Change"
    subcategories:
      - software-architecture
---

[First principles](https://en.wikipedia.org/wiki/First_principle) thinking breaks a problem into truths you cannot deduce further, then rebuilds a solution from those foundations. We **adopt** it for **[[Software Architecture]]** and design review when inherited patterns no longer match constraints. It is the forward-looking counterpart to **[[Five Whys]]** in blameless postmortems. Still **assess** each decision before applying the method by rote outside design work.

## Blurb

> A first principle is a basic proposition or assumption that cannot be deduced from any other proposition or assumption.

## Summary

Use first principles when a design copies industry defaults ("always microservices", "always one Terraform module") and cost, latency, or ownership no longer fit. The goal is not novelty for its own sake. The goal is to name constraints that must stay true, then pick a shape that satisfies them.

| Context                                  | Garden stance                                   |
| ---------------------------------------- | ----------------------------------------------- |
| **Design and architecture reviews**      | **Adopt** as the default reasoning method       |
| **Ops, hiring, tooling, one-off tasks**  | **Assess** before investing deconstruction time |
| **Mature pattern with known trade-offs** | **[[Reasoning by analogy]]** is often enough    |

**Assumptions section:** Add an explicit **Assumptions** block to design docs. Use it to open review conversation. If reviewers debate an assumption, it is not a first principle yet. Deconstruct until the team agrees on bedrock constraints, then rewrite the design if needed.

**Sibling techniques:** **[[Five Whys]]** and **[[Fishbone diagram]]** trace failures backward in postmortems. First principles trace forward when you still control the shape.


## Details

### Design Review Checklist

1. List constraints the solution must satisfy (latency, blast radius, compliance, team ownership).
2. Write **Assumptions** separately from constraints. Assumptions are hypotheses; constraints are non-negotiable unless disproven.
3. In review, challenge any assumption that draws debate. Convert surviving items into first principles or remove them.
4. Rebuild the proposal from the agreed principles. Name **[[Design Pattern]]** choices only after the shape is clear.

### When Not to Use

- Small, reversible changes with known precedent
- Decisions where time-to-ship matters more than architectural purity
- Problems better served by empirical measurement than upfront deconstruction

### Related Notes

- **[[Single Responsibility Principle]]** for module-level "one reason to change"
- **[[Design Pattern]]** vocabulary after structure is chosen, not before
- **[[Incident Management]]** for the postmortem side of the same learning loop
