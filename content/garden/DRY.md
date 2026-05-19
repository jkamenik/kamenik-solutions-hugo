---
title: "DRY"
date: 2025-01-05
lastmod: 2026-05-18
draft: false

keywords:
  - DRY
  - Don't Repeat Yourself

params:
  garden:
    kind: item
    usefulness: hold
    category: technique
    movement: "Moved Out"

aliases:
  - /radar/techniques/dry
---

[Don't Repeat Yourself (DRY)](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) says every piece of knowledge should have a single, authoritative representation in a system. We rate **hold** with **Moved Out**: treat DRY as a **smell to investigate**, not a mandate to abstract. Duplication is often cheaper than the wrong shared abstraction, especially in **[[IaC]]** where blast radius matters more than line count.

## Blurb

> Every piece of knowledge must have a single, unambiguous, authoritative representation within a system.

## Summary

**What DRY gets right:** copy-pasted logic drifts; two sources of truth for the same rule will disagree; fixes get applied in one place and missed in another.

**Where DRY goes wrong:**

| Pitfall | Effect |
|---------|--------|
| **Premature abstraction** | One helper for two cases that later diverge |
| **False equivalence** | "Looks the same" code with different change reasons |
| **Mega-modules** | Terraform/Helm modules that couple unrelated resources |
| **Imperative escape hatch** | "Not DRY enough" pushes teams to **[[Imperative IaC]]** (**hold**) |

**Better heuristics (not garden items yet):**

- **Rule of Three:** duplicate until the third similar case proves the abstraction.
- **AHA:** avoid hasty abstractions; let structure emerge from real variation.
- **WET in IaC:** a little repetition keeps plans readable and limits coupling.

**Garden alignment:** **[[Declarative IaC]]** (**adopt**) stays DRY *enough* via modules, variables, `for_each`, Helm subcharts, and policy bundles without generating infrastructure from application languages. Repetition is a design smell, not a reason to adopt CDK/Pulumi.

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

**Garden pattern:** **hold** DRY as a default team slogan; **Moved Out** from treating it as a top-level principle. Prefer **[[Declarative IaC]]** composition tools over imperative generators justified only by DRY.

**References**

- [Wikipedia: Don't repeat yourself](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
- [Please do repeat yourself: DRY is dead](https://dev.to/ralphcone/please-do-repeat-yourself-dry-is-dead-1jbg)
- [The fallacy of DRY](https://dev.to/jeroendedauw/the-fallacy-of-dry)
