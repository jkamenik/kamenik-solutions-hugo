---
title: "Codacy"
date: 2023-07-23
lastmod: 2026-05-18
draft: false

keywords:
  - Codacy

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "No Change"
    subcategories:
      - code-scanner

aliases:
  - /radar/tools/codacy
---

[Codacy](https://www.codacy.com) is a **[[Software as a Service]]** code-quality and security platform that runs on **[[Pull Request]]**s, aggregates many linters and SAST rules, and surfaces grades and trends. We rate it **assess**: strong when you want a unified quality dashboard and policy gates across repos; for "fail the build on lint violations" in **[[GitHub Actions]]**, **[[Super-Linter]]** (container in CI) is simpler and free.

## Blurb

> Security and Code Quality for AI-Accelerated Coding
>
> Codacy enforces security and quality standards across the entire CI/CD. Build secure, compliant and maintainable software, from IDE to Runtime.

## Summary

**Role:** PR-time **[[Code Scanner]]** under **[[Code Linting]]** / **[[Shift Left]]**: duplicate findings from ESLint, Bandit, Trivy-style checks, etc. into one UI, with org-level quality gates and coverage metrics.

**When to assess:** many repos and languages, need central reporting for engineering leaders, or evaluating consolidation vs running linters directly in CI.

**When to skip:** small teams with one stack; you only need deterministic lint fail in pipeline (use **[[Super-Linter]]** or language-native linters); IaC/policy validation (**[[Conftest]]**, **trial**) is a separate concern.

**Pairs with:** **[[DevSecOps]]** program (treat findings as backlog, not theater); required checks on `main`; do not replace secret scanning, dependency review, or **[[Policy as Code]]** on infra.

**Not the same as:** SCA-only vendors, DAST, or OPA/Conftest for Terraform/K8s manifests.

## Details

| Topic | Notes |
|-------|--------|
| **Integration** | GitHub/GitLab/Bitbucket apps; status checks on PRs |
| **Findings** | Severity, patterns, optional AI-assisted triage (verify noise) |
| **Coverage** | Test coverage tracking; useful for trends, not a substitute for good tests |
| **Config** | `.codacy.yml` / UI policies; align with team **[[Code Linting]]** standards |
| **Cost** | Per-seat SaaS; compare TCO vs OSS linters in **[[GitHub Actions]]** |

**Garden pattern:** default local/CI lint (**adopt** **[[Code Linting]]** + Super-Linter in Actions). Pilot Codacy when visibility across dozens of services justifies another vendor.

**References**

- [Codacy](https://www.codacy.com/)
- [Super-Linter](https://github.com/super-linter/super-linter) (alternative)
