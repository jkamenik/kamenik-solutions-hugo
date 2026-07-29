---
title: DRY
date: '2025-01-05'
lastmod: '2026-07-29'
draft: false
keywords:
- DRY
- "Don't Repeat Yourself"
params:
  aliases:
  - "Don't Repeat Yourself"
  garden:
    kind: item
    usefulness: hold
    category: technique
    movement: Moved Out
aliases:
- /radar/techniques/dry
---

[DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) is a technique we **hold** in the garden.

## Summary

**Key points:**

| Context | Guidance |
|---------|----------|
| **Application code** | Extract when behavior and change rate align; keep tests on both call sites during migration |
| **Terraform / OpenTofu** | Prefer small modules with clear inputs/outputs over one module that owns an entire account |
| **Kubernetes / Helm** | Subcharts for real reuse; copy YAML when teams and lifecycles differ |
| **Policies** | One Rego/Sentinel bundle per concern; do not merge unrelated checks for line count |
| **Reviews** | Ask "what changes together?" not "how many times does this string appear?" |

**IaC-specific:** minimizing blast radius beats minimizing bytes. Explicit duplication in two stacks is often **safer** than a shared module that forces unrelated environments to upgrade together.

**When repetition is OK:** similar HCL for dev and prod with intentional differences; two resources that look alike but have different owners or compliance tags; bootstrap code you expect to delete.

**References**

- [Wikipedia: Don't repeat yourself](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
- [Please do repeat yourself: DRY is dead](https://dev.to/ralphcone/please-do-repeat-yourself-dry-is-dead-1jbg)
- [The fallacy of DRY](https://dev.to/jeroendedauw/the-fallacy-of-dry)## Personal Experience

<!-- User-owned: vault-only; never published or exported. Agents read for /tech-garden update synthesis; proofread spelling/grammar only. -->

## Details

| Context | Guidance |
|---------|----------|
| **Application code** | Extract when behavior and change rate align; keep tests on both call sites during migration |
| **Terraform / OpenTofu** | Prefer small modules with clear inputs/outputs over one module that owns an entire account |
| **Kubernetes / Helm** | Subcharts for real reuse; copy YAML when teams and lifecycles differ |
| **Policies** | One Rego/Sentinel bundle per concern; do not merge unrelated checks for line count |
| **Reviews** | Ask "what changes together?" not "how many times does this string appear?" |

**IaC-specific:** minimizing blast radius beats minimizing bytes. Explicit duplication in two stacks is often **safer** than a shared module that forces unrelated environments to upgrade together.

**When repetition is OK:** similar HCL for dev and prod with intentional differences; two resources that look alike but have different owners or compliance tags; bootstrap code you expect to delete.

**References**

- [Wikipedia: Don't repeat yourself](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
- [Please do repeat yourself: DRY is dead](https://dev.to/ralphcone/please-do-repeat-yourself-dry-is-dead-1jbg)
- [The fallacy of DRY](https://dev.to/jeroendedauw/the-fallacy-of-dry)
