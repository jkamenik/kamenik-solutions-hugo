---
title: CUE
date: '2025-07-10'
lastmod: '2026-07-28'
draft: false
keywords:
- CUE
- CUE lang
- cuelang
params:
  aliases:
  - CUE lang
  - cuelang
  garden:
    kind: item
    usefulness: assess
    category: code
    movement: No Change
    subcategories:
    - language
---

[CUE](https://cuelang.org) is a constraint-based language for validating, unifying, and generating structured data (JSON, YAML, TOML, and more). We **assess** it when **[[JSON Schema]]** and **[[OpenAPI]]** are not enough, but we do not default to it for new work.

## Blurb

> CUE makes it easy to validate data, write schemas, and ensure configurations align with policies.

## Summary

**What it is:** Configure, Unify, Execute. CUE merges schemas through unification, validates with `cue vet`, and exports to **[[JSON Schema]]**, OpenAPI, and Kubernetes CRD shapes. Influenced by Google's internal GCL/BCL lineage (see **Details**).

**When to use:**

| Situation | Notes |
|-----------|--------|
| Cross-format validation | One schema for JSON, YAML, and CUE inputs in CI |
| Policy patches | Separate base schema from version-specific constraints; CUE merges and reports conflicts |
| Kubernetes CRDs | Generate structural OpenAPI from concise CUE definitions |
| Go or Protobuf drift | `cue import` from **[[GoLang]]** or **[[Protobuf]]** types |

**When to skip:**

- Standard API or config validation (**[[JSON Schema]]** **adopt** is the default)
- Teams without appetite for another config language
- Estates already standardized on **[[HCL]]**, **[[YAML]]** templates, or **[[Conftest]]** + Rego
- Greenfield work where schema tooling is not the bottleneck

**Trade-offs:** Powerful but niche. Another standards-layer risk (XKCD 927). Smaller ecosystem than JSON Schema. Worth studying even when you do not adopt, because it demonstrates how constraint unification can replace verbose schema boilerplate.

## Details

### Core Commands

| Command | Role |
|---------|------|
| `cue vet` | Validate data files against CUE schemas |
| `cue export` | Emit JSON, YAML, or other targets from unified values |
| `cue import` | Pull types from Go, JSON Schema, OpenAPI, Protobuf |
| `cue fmt` | Format CUE sources |

Schemas and policies can live in separate `.cue` files. CUE unifies them before validation.

### Compared to **[[JSON Schema]]**

| Topic | CUE | JSON Schema |
|-------|-----|-------------|
| Verbosity | Concise constraints, unification | Verbose for complex cross-field rules |
| Ecosystem | Growing; Kubernetes and OpenAPI bridges | **Adopt** everywhere in our pipelines |
| Learning curve | New language semantics | Familiar to most platform engineers |
| Garden stance | **assess** | **adopt** |

### GCL Lineage

CUE draws from Google's internal General Config Language (GCL) and related BCL work. Even if you never deploy CUE, reading the design explains how Google-style config unification differs from template sprawl. Public background: [General Config Language paper (PDF)](https://pure.tue.nl/ws/portalfiles/portal/46927079/638953-1.pdf).

### References

- [CUE documentation](https://cuelang.org/docs/)
- [Language specification](https://cuelang.org/docs/reference/spec/)
- [GitHub: cue-lang/cue](https://github.com/cue-lang/cue)
