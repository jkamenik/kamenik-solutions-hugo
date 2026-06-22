---
title: "Semgrep"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - Semgrep

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
    subcategories:
      - code-scanner
---

[Semgrep](https://semgrep.dev) is a fast static analysis platform for SAST, dependency scanning, and secrets detection across 30+ languages. Rules look like source code, so teams can encode custom security and style checks. We **trial** it under **[[Code Scanner]]** for PR and CI guardrails when **[[Code Linting]]** alone is not enough. The open-core CLI is free; advanced cross-file analysis and platform features sit in the commercial AppSec Platform.

## Blurb

> Find bugs and reachable dependency vulnerabilities in code. Enforce your code standards on every commit.

## Summary

**When to use:** you want pattern-based SAST with a large shared rule registry; fast local and CI scans on **[[Pull Request]]**s; optional SaaS triage, SCA reachability, and secrets validation via Semgrep AppSec Platform.

**When to skip:** Terraform or K8s policy only (use **[[Conftest]]**); org wants a fully OSS engine without commercial tier splits (see **[[OpenGrep]]**); you need deep enterprise SAST with minimal rule tuning (compare **[[Codacy]]** or vendor SAST).

**Open vs commercial:** Community Edition (CE) CLI covers single-file and single-function analysis. Pro Engine and the AppSec Platform add cross-function and cross-file taint, AI triage, autofix PRs, and supply-chain reachability. Semgrep tightened CE limits in late 2024, which spurred the **[[OpenGrep]]** fork.

**Pairs with:** **[[SARIF]]** output for unified dashboards; **[[GitHub Actions]]** or any CI; **[[Shift Left]]** required checks before merge.


## Details

| Topic | Notes |
|-------|--------|
| **Rule format** | YAML rules with metavariables; patterns mirror target language syntax |
| **Run modes** | IDE, pre-commit, `semgrep scan`, `semgrep ci` with managed rules |
| **Languages** | 30+ including Python, Go, Java, JavaScript, TypeScript, Terraform, YAML |
| **Registry** | [semgrep.dev/r](https://semgrep.dev/r) community and vendor rules |
| **License** | Engine LGPL-2.1; some rules and platform features are commercial |

**References**

- [Semgrep documentation](https://semgrep.dev/docs/)
- [semgrep/semgrep on GitHub](https://github.com/semgrep/semgrep)
