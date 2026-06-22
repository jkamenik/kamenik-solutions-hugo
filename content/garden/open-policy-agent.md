---
title: "Open Policy Agent"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - Open Policy Agent
  - OPA
  - Open Policy Agent (OPA)

params:
  aliases:
    - OPA
    - Open Policy Agent (OPA)
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: "New"
---

[Open Policy Agent](https://www.openpolicyagent.org/) (OPA) is a CNCF policy engine that evaluates Rego policies against JSON inputs. It powers **[[Conftest]]** on PRs, **[[Gatekeeper]]** in **[[Kubernetes]]** admission, and many CI gates. We **adopt** OPA as the default engine for **[[Policy as Code]]** when rules need shared language across repos and clusters.

## Blurb

> Open Policy Agent (OPA) is an open source, general-purpose policy engine.

## Summary

**What it is:** Policy decision point with Rego language, bundle distribution, and integrations as sidecar, admission webhook, or CLI library.

**When to use:** Same policy must run in CI (**[[Conftest]]**), admission (**[[Gatekeeper]]**), and API authorization layers.

**When to skip:** Trivial one-off checks better served by **[[CEL]]** native validation or linters without Rego ops.

**Key features:** `opa test`, bundle signing, decision logs, WASM compilation for embedded checks.


## Details

| Topic | Notes |
|-------|--------|
| **Runners** | **[[Conftest]]** for files on disk; **[[Gatekeeper]]** for live cluster admission |
| **Practice** | Version policy bundles; test Rego in CI; avoid unbounded policy complexity |

**References**

- [OPA documentation](https://www.openpolicyagent.org/docs)
- [Rego language](https://www.openpolicyagent.org/docs/latest/policy-language/)
