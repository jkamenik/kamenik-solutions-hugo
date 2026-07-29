---
title: Spec-Driven Development (SDD)
date: '2026-07-23'
lastmod: '2026-07-29'
draft: false
keywords:
- Spec-Driven Development (SDD)
- SDD
params:
  aliases:
  - SDD
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - ai-techniques
---

Spec-driven development makes a reviewed specification the source of truth for planning, implementation, and validation. We **adopt** it as the working successor to **[[TDD]]** and **[[BDD]]**: the agent is part of the spec, and the spec still carries testable behavior in plain text.

## Summary

SDD extends **[[BDD]]**, which extended **[[TDD]]**. TDD locked behavior in tests first. BDD required those tests to describe desired behavior in plain text. SDD keeps that content and adds the agent as a first-class participant in the specification.

**Lineage:** **[[TDD]]** (**hold**) → **[[BDD]]** (**hold**) → **SDD** (**adopt**).

**What a good SDD spec must include (from TDD/BDD):**

| From | Carry into the spec |
|------|---------------------|
| **[[TDD]]** | Concrete cases, edge variants, and acceptance that **[[Unit Testing]]** can lock |
| **[[BDD]]** | Plain-text behavior and scenarios (who, when, then), not jargon-only checks |
| SDD | Agent role, constraints, exclusions, and how the agent validates against the spec |

**When to use:**

| Situation | Notes |
|-----------|--------|
| Multi-file or architectural work | Agree on intent before agents or people code |
| Ambiguous requirements | Grill assumptions before a plan exists |
| Living product direction | Update the spec when truth changes; keep history in ADRs |

**When to skip:**

- Trivial, easily reversed changes that are already fully understood
- Documentation cost exceeds the value of the change

**Keep it living:** Update the specification when requirements change. Record significant architectural changes with [[Architecture Decision Record (ADR)|ADRs]] instead of silently rewriting history.

**Stay tool-independent:** The practice matters more than any template, command set, or coding agent. [[GitHub Spec Kit]] is one scaffold, not the definition of SDD.

Related: [[Specification]], [[AI Techniques]], [[GitHub Spec Kit]], [[Unit Testing]], [[TDD]], [[BDD]].

## Details

A practical SDD loop has five stages:

1. **Specify:** define the problem, desired outcomes, constraints, exclusions, and acceptance criteria. Include plain-text behaviors and testable cases (BDD/TDD content).
2. **Clarify:** challenge assumptions and resolve questions that would materially change the solution.
3. **Plan:** choose an implementation approach and record significant architectural decisions.
4. **Implement:** break the plan into verifiable tasks, then execute them against the specification (agent and/or people).
5. **Validate:** compare the result with the acceptance criteria; use **[[Unit Testing]]** where logic belongs.

Specifications should describe intent without prematurely locking every implementation detail. Plans and ADRs capture technical decisions while the specification stays on behavior and constraints.

The specification is a living artifact, but it should not erase decision history. When a requirement or architecture changes, update the current truth and preserve the rationale in an ADR or timeline.
