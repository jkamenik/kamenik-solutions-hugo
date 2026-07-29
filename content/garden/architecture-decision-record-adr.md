---
title: Architecture Decision Record (ADR)
date: '2026-07-23'
lastmod: '2026-07-23'
draft: false
keywords:
- Architecture Decision Record (ADR)
- ADR
- ADRs
- Architecture Decision Records
params:
  aliases:
  - ADR
  - ADRs
  - Architecture Decision Records
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - software-architecture
---

[Architecture Decision Record (ADR)](https://www.cognitect.com/blog/2011/11/15/documenting-architecture-decisions)

An [Architecture Decision Record](https://www.cognitect.com/blog/2011/11/15/documenting-architecture-decisions) captures one significant architectural decision, its context, and its consequences. We **adopt** ADRs because AI-assisted delivery increases the need to preserve why a system took its current shape.

## Summary

ADRs preserve decision rationale near the system they describe. Each record explains the forces behind a decision, the choice made, and the expected consequences.

- **Use when:** a decision changes system structure, constraints, technology choices, or long-term operating costs.
- **Pair with SDD:** use ADRs alongside [[Spec-Driven Development (SDD)]] to preserve architectural rationale while the specification remains current.
- **Keep them close:** store ADRs in the project repository so changes can follow the normal review process.
- **Preserve history:** mark an obsolete ADR as deprecated or superseded. Create a new record instead of rewriting the original decision.
- **Skip when:** the choice is trivial, easily reversed, or already explained by an established standard.

Related garden notes: [[Software Architecture]], [[Spec-Driven Development (SDD)]], [[Specification]], and [[Design Pattern]].

## Details

Michael Nygard's original format uses five parts:

| Part | Purpose |
|------|---------|
| Title | Name the decision, not merely the problem |
| Status | Track proposed, accepted, deprecated, or superseded decisions |
| Context | Describe the facts and forces that require a decision |
| Decision | State the chosen response in active voice |
| Consequences | Record positive, negative, and neutral outcomes |

One ADR should cover one significant decision. The context should remain value-neutral, while the decision should state what the team will do.

Record every meaningful consequence, not only the benefits. Those consequences often become context for later decisions.

A replacement decision should reference the ADR it supersedes. The old ADR should point forward to its replacement, preserving a navigable decision history.

### ADRs and Spec-Driven Development

A specification should show the current intent. ADRs should preserve why significant architectural choices were made as that intent evolves.

AI agents can maintain both artifacts, but the team remains responsible for approving the decision. An agent should update links and status without erasing the original context or consequences.
