---
title: "OpenGrep"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - OpenGrep

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - code-scanner
---

[OpenGrep](https://github.com/opengrep/opengrep) is a community fork of Semgrep CE, created in January 2025 after Semgrep moved several engine capabilities behind a commercial license. It targets backward compatibility with Semgrep YAML rules and JSON or **[[SARIF]]** output. We **assess** it under **[[Code Scanner]]** when a vendor-neutral OSS engine matters more than Semgrep Inc.'s platform roadmap.

## Blurb

> Opengrep is the most advanced open source SAST engine. Analyze large code bases at the speed of thought with intuitive pattern matching and customizable rules.

## Summary

**When to use:**

- You already run Semgrep rules and want CE-era engine features without a login
- You need cross-function taint, restored SARIF fingerprints, or native Windows support in OSS
- You prefer a multi-vendor consortium over a single vendor's open-core split

**When to skip:** you want managed triage, SCA reachability, secrets validation, or AI autofix (stay on Semgrep AppSec Platform); you need the widest rule registry and vendor support today (**[[Semgrep]]** still leads mindshare).

**Greenfield:** either engine is fine; pilot both on the same rule pack.

**Fork context:** branched from Semgrep v1.100.0 (December 2024). Backers include Aikido, Endor Labs, Jit, Orca Security, and others. Goal is a foundation-governed engine with pro-only CE gaps reopened (cross-function analysis, extended languages, fingerprint metadata).

**Pairs with:** existing Semgrep CI configs (often drop-in); **[[GitHub Actions]]**; **[[Shift Left]]** gates on **[[Pull Request]]**s.


## Details

| Topic | Notes |
|-------|--------|
| **Compatibility** | Semgrep rule syntax; common CLI flags; JSON and SARIF outputs |
| **Engine focus** | OCaml 5 parallelism, faster taint, extra languages (VB, Apex, Elixir) |
| **Distribution** | GitHub releases; also bundled in tools like Codacy (`opengrep` engine) |
| **License** | LGPL-2.1 |
| **Governance** | Consortium-backed; roadmap toward foundation stewardship |

**vs [[Semgrep]]:** Semgrep ships faster platform features (AI detection, supply chain, secrets). OpenGrep optimizes for OSS engine depth and rule portability. Semgrep has since added OCaml 5 and Windows support too; treat performance claims as benchmark-dependent.

**References**

- [opengrep/opengrep on GitHub](https://github.com/opengrep/opengrep)
- [OpenGrep site](https://opengrep.dev/)
