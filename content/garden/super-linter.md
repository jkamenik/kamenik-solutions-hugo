---
title: Super-Linter
date: '2024-10-01'
lastmod: '2026-07-29'
draft: false
keywords:
- Super-Linter
params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: No Change
---

[Super-Linter](https://github.com/super-linter/super-linter) runs many language linters from one Docker image, as a **[[GitHub Actions]]** job or standalone. We **adopt** it for free, tunable multi-language quality gates in CI.

## Blurb

> Combination of multiple linters to run as a GitHub Action or standalone.

## Summary

**What it is:** Detects file types in the repo and enables matching linters. Tunable via in-repo config. Practical OSS alternative to commercial multi-language scanners for style and static checks.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Polyglot repos | One Action covers many languages without N separate jobs |
| Bootstrap quality | Fast first gate before deeper SAST/SCA products |
| Local + CI parity | Same image locally and in **[[GitHub Actions]]** |

**When to skip:**

- Single-language repos already covered by one well-tuned linter
- Need deep security/SCA findings (pair with dedicated tools; do not expect Super-Linter alone)
- Image size / cold start dominates a tiny pipeline

**Trade-offs:** Engineers resist lint noise; start with a narrow allowlist and grow. Free and flexible, but you own rule hygiene. Complements, does not replace, Codacy-class platforms when those are already paid for.

## Details

| Topic | Notes |
|-------|--------|
| Runtime | Docker image; GitHub Action or CLI |
| Config | Per-linter files and env flags in-repo |
| Home | Org moved to `super-linter/super-linter` (was `github/super-linter`) |

**References**

- [super-linter/super-linter](https://github.com/super-linter/super-linter)
