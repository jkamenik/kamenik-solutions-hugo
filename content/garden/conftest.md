---
title: "Conftest"
date: 2024-10-01
lastmod: 2026-06-12
draft: false

keywords:
  - Conftest

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "No Change"
    subcategories:
      - code-scanner
aliases:
  - /radar/tools/conftest
---

[Conftest](https://www.conftest.dev) is a CLI that runs [Open Policy Agent](https://www.openpolicyagent.org/) (Rego) policies against structured config on disk: Terraform plans, Kubernetes manifests, Helm charts, Tekton, Dockerfile, and more. We **trial** it under **[[Code Scanner]]** as the default way to implement **[[Policy as Code]]** in CI before deploy; **[[Policy as Code]]** itself is **adopt** as a **[[Technique]]**.

## Blurb

> Conftest helps you write tests against structured configuration data. Using Conftest you can write tests for your Kubernetes configuration, Tekton pipeline definitions, Terraform code, Serverless configs or any other config files.

## Summary

**Role:** offline policy tests (`conftest test`, `conftest verify`) with policies in Rego, results as pass/fail per file. Fits **[[Shift Left]]** and **[[DevSecOps]]** build gates on **[[Pull Request]]**s via **[[GitHub Actions]]** (or any CI).

**When to use:** you already commit IaC and want repeatable compliance rules; OPA ecosystem is acceptable; need one tool across Terraform + K8s + misc YAML.

**When to skip:** only application source linting (use **[[Code Linting]]** / **[[Codacy]]**); Terraform-only teams may **assess** **[[Regula]]** instead; simple Kubernetes admission without OPA ops may use native **[[CEL]]** (`ValidatingAdmissionPolicy`) for narrower rules.

**Pairs with:** versioned `policy/` repo or directory; `conftest verify` for policy unit tests; admission controllers in-cluster for runtime (Conftest is pre-deploy).

**Not the same as:** **[[Codacy]]** (multi-linter SaaS on app repos); cluster admission webhooks (different execution point).

## Details

| Topic | Notes |
|-------|--------|
| **Inputs** | Directories of manifests, JSON/YAML, HCL, Dockerfile, etc. |
| **Policies** | Rego under `policy/`; share bundles with OPA elsewhere |
| **CI** | Fail build on deny; pin Conftest version in workflow |
| **Terraform** | Test planned JSON (`terraform show -json`) or static `.tf` per your pipeline |
| **Helm** | Render chart then test output, or test templates with care |
| **Learning curve** | Rego is the cost; invest once for cross-surface rules |

**References**

- [Conftest documentation](https://www.conftest.dev/)
- [Open Policy Agent](https://www.openpolicyagent.org/)
