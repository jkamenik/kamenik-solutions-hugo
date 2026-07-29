---
title: TDD
date: '2026-07-29'
lastmod: '2026-07-29'
draft: false
keywords:
- TDD
- Test-Driven Development
- Test Driven Development
params:
  aliases:
  - Test-Driven Development
  - Test Driven Development
  garden:
    kind: item
    usefulness: hold
    category: technique
    movement: No Change
---

[Test-driven development (TDD)](https://en.wikipedia.org/wiki/Test-driven_development) is the red-green-refactor loop: write failing automated test, make it pass, then clean up. We **hold** it for new process design: **[[BDD]]** extended it, and **[[Spec-Driven Development (SDD)]]** replaced both as the working practice.

## Blurb

> Test-driven development is a software development process relying on software requirements being converted to test cases before software is fully developed, and tracking all software development by repeatedly testing the software against all test cases.

## Summary

**What it is:** A programming workflow popularized by Kent Beck. List expected behavior variants, write one automated test, make it pass, optionally refactor.

**Lineage:** TDD → **[[BDD]]** (plain-text behavior) → **[[Spec-Driven Development (SDD)]]** (spec includes agent). Do not start new work as classic TDD-only. Carry TDD's testable cases into the SDD specification and still ship **[[Unit Testing]]**.

**When to use (existing only):**

| Situation | Notes |
|-----------|--------|
| Inherited TDD culture | Keep green suites; migrate process toward SDD |
| Teaching history | Explain red-green-refactor as the root of BDD/SDD |

**When to skip (new work):**

- Greenfield delivery process: use **[[Spec-Driven Development (SDD)]]**
- Intent and acceptance belong in the spec, not only in programmer-facing tests

**Trade-offs:** TDD taught fast feedback and test-first design. Alone it under-serves agent workflows and shared plain-text behavior. Those jobs moved up the lineage.

## Details

Canonical loop (Beck-style):

1. List expected variants of the new behavior
2. Write one failing automated test
3. Change the system until the test passes
4. Optionally refactor; keep green

What SDD must still capture from TDD: concrete, testable cases and edge variants that units can lock.

**References**

- [Test-driven development (Wikipedia)](https://en.wikipedia.org/wiki/Test-driven_development)
- [Kent Beck: Canon TDD](https://newsletter.kentbeck.com/p/canon-tdd)
