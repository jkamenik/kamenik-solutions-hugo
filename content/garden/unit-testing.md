---
title: Unit Testing
date: '2026-01-08'
lastmod: '2026-07-29'
draft: false
keywords:
- Unit Testing
params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
---

[Unit testing](https://en.wikipedia.org/wiki/Unit_testing) verifies the smallest testable pieces of software in isolation. We **adopt** it as the default fast feedback layer. Process defaults to **[[Spec-Driven Development (SDD)]]**; **[[TDD]]** and **[[BDD]]** are **hold** predecessors whose testable cases still belong in the spec.

## Summary

**What it is:** Automated checks on functions, classes, or modules with controlled dependencies (fakes, stubs, mocks). Fast, deterministic, and owned by the same team that writes the code.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Business logic and pure functions | Highest ROI; few collaborators |
| Regression safety on refactors | Lock behavior before structural change |
| Agent-written code | SDD spec + units catch drift early |
| Cases called out in the SDD spec | Implement the TDD/BDD content as real tests |

**When to skip (or de-emphasize):**

- Behavior only meaningful across process or network boundaries (use **[[Integration Testing]]**)
- UI chrome with no logic (prefer fewer brittle tests)
- Prototypes you will throw away the same day

**Trade-offs:** Too many mocks hide integration bugs. Too few units leave slow suites as the only safety net. Aim for a pyramid: many units, fewer integrations, sparse end-to-end.

**Related practices:** **[[Spec-Driven Development (SDD)]]** (**adopt**) owns intent and includes the agent. **[[TDD]]** / **[[BDD]]** (**hold**) describe the lineage; their plain-text behaviors and cases should appear in the SDD spec, then land as units here.

## Details

| Related practice | Role |
|------------------|------|
| **[[Spec-Driven Development (SDD)]]** | Spec intent (incl. agent); units verify logic |
| **[[TDD]]** (**hold**) | Historical test-first loop; cases still belong in the spec |
| **[[BDD]]** (**hold**) | Historical plain-text behavior; scenarios still belong in the spec |
| **[[Integration Testing]]** | Verify seams units intentionally fake |

**References**

- [Unit testing (Wikipedia)](https://en.wikipedia.org/wiki/Unit_testing)
