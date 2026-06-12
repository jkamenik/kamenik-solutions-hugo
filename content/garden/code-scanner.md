---
title: "Code Scanner"
date: 2026-05-17
lastmod: 2026-05-18
draft: false

keywords:
  - Code Scanner

params:
  garden:
    kind: subcategory
    parent_category: tool
    subcategory_slug: code-scanner
---

Under **[[Tool]]**, **Code Scanner** groups products that **analyze source, dependencies, or committed config** and report findings (usually on **[[Pull Request]]**s or in CI). This is the vendor and runner layer; the practice of enforcing standards is **[[Code Linting]]** (**adopt** as a **[[Technique]]**).

**What belongs here:**

| Kind | Examples in the garden |
|------|-------------------------|
| PR / repo quality platforms | **[[Codacy]]** (**assess**): aggregated linters, SAST, coverage dashboards |
| Config / IaC policy runners | **[[Conftest]]** (**trial**): **[[Open Policy Agent]]** tests on Terraform, K8s, etc. |
| Language-native SAST (future items) | Semgrep-class tools when we add them |

**What does not belong here:**

- **[[Code Linting]]** the technique (how teams enforce style and static rules).
- **[[Super-Linter]]** and bare ESLint/golangci-lint configs (run via **[[Code Linting]]** + **[[GitHub Actions]]**, not a scanner SKU).
- **DAST** against running apps (**[[Zed Attack Proxy (Zap)]]** is dynamic testing, not repo scanning).
- **[[Unit Testing]]** / **[[Integration Testing]]** (behavior verification).

**Garden stance:**

- Default: **[[Code Linting]]** in-repo + **[[Super-Linter]]** (or per-language linters) in **[[GitHub Actions]]** with required PR checks.
- **assess** **[[Codacy]]** when you need org-wide quality scores across many repos.
- **trial** **[[Conftest]]** when **[[Policy as Code]]** on IaC is the goal; pair with **[[Shift Left]]** and **[[DevSecOps]]** stages (build/test gates, not checkbox compliance).

Tag a **product** here when the primary artifact is a scanner service or CLI marketed for security/quality analysis. Tag **[[CI-CD Tools]]** when the product is primarily a pipeline server (Jenkins, Actions).
