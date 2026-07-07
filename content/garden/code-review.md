---
title: Code Review
date: '2025-04-09'
lastmod: '2026-07-02'
draft: false
keywords:
- Code Review
params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
aliases:
- /radar/techniques/code-review
---

[Code Review](https://en.wikipedia.org/wiki/Code_review). Is structured peer (or self) inspection of a change before it lands on the mainline.

## Summary

**What good review looks like:** small, focused diffs; clear description; at least one qualified reviewer when possible; all automated checks green; unresolved comments block merge.

**Workflow:** hosts such as **[[GitHub]]** and **[[GitLab]]** implement review via **[[Pull Request]]** / Merge Request; Gerrit uses change-based review with similar gates. The PR is the front door to **[[Continuous Integration]]**: nothing merges until review and CI agree.

**Machine vs human:**

| Layer | Catches | Garden links |
|-------|---------|--------------|
| Automated | Style, static bugs, policy, unit tests | **[[Code Linting]]**, **[[Conftest]]**, **[[Codacy]]** (assess) |
| Human | Architecture, security nuance, operability, product fit | This technique |

**Solo developers:** still open a PR against `main`; bots and CI play the second pair of eyes.

**Pairs with:** **[[Shift Left]]** (find issues before production); **[[DevSecOps]]** (security findings are review backlog, not theater).

## Details

| Topic | Notes |
|-------|--------|
| **Size** | Prefer PRs that fit one context switch; split large work |
| **Blocking** | Failed checks, policy denies, or open required threads = no merge |
| **Rubber stamps** | Review for understanding, not checkbox approval |
| **Ownership** | CODEOWNERS or team routing for sensitive paths |
| **AI-assisted code** | Higher bar for human review; never skip automation |

**Terminology:** see **[[Pull Request]]** (GitHub PR, GitLab MR). Same practice, different vendor names.

**References**

- [Wikipedia: Code review](https://en.wikipedia.org/wiki/Code_review)
