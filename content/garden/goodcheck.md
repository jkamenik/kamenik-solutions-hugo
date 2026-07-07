---
title: goodcheck
date: '2026-05-27'
lastmod: '2026-07-02'
draft: false
keywords:
- goodcheck
params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: No Change
    subcategories:
    - code-scanner
aliases:
- /radar/tools/goodcheck
---

[goodcheck](https://sider.github.io/goodcheck/) is a tool we use to limit standing privilege and grant audited, time-bound access instead. We **hold** it under **[[Tool]]** in the garden.

## Summary

**When it was useful:** enforce house style ("do not call X", "prefer Y over Z") without standing up a full SAST platform; fast feedback in CI.

**When to skip now:** greenfield adoption. Prefer Semgrep-class rule runners or language-native linters with active maintenance.

**Still available (frozen):** Ruby gem `goodcheck` 3.1.0 on RubyGems (last release 2021-07-15). Docs at [sider.github.io/goodcheck](https://sider.github.io/goodcheck/). Docker image `sider/goodcheck` appears removed from Docker Hub.

**Alternatives:** Semgrep, custom grep/regex CI steps, **[[Conftest]]** / OPA for policy on IaC (not a drop-in for app-source YAML rules).

## Details

### History

| Era | Org / repo | Notes |
|-----|------------|-------|
| 2014-2018 | SideCI | Tokyo-based automated PR review product |
| 2018+ | Sider (`sider/goodcheck`) | Rebrand; goodcheck open-sourced as AGPL Ruby gem |
| 2022-09 | Service shutdown | sider.review end-of-service (see Web Archive) |
| 2025-03 | Company liquidation | 株式会社 Sider wound up; GitHub org repos deleted |

### Rule shape (for comparison)

Rules are YAML lists with `id`, `pattern` (regex), `message`, optional `glob`, `pass`/`fail` examples. Same niche as lightweight custom Semgrep rules, but with a smaller ecosystem.

### Status

**Abandoned, not renamed.** Sider ended its code-review service in September 2022. The company (株式会社 Sider) completed liquidation on 2025-03-04. `github.com/sider/goodcheck` and the earlier `sideci/goodcheck` both return 404. There is no official successor repo or maintained fork with comparable traction.
