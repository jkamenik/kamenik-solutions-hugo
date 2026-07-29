---
title: Regula
date: '2024-10-01'
lastmod: '2026-07-29'
draft: false
keywords:
- Regula
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - code-scanner
---

[Regula](https://regula.dev) is an OPA/Rego CLI that scans IaC for cloud and Kubernetes misconfigurations before deploy. We **assess** it as one path under **[[Policy as Code]]**, beside **[[Checkov]]** and raw **[[Open Policy Agent]]**.

## Blurb

> Regula is a tool that evaluates infrastructure as code files for potential AWS, Azure, Google Cloud, and Kubernetes security and compliance violations prior to deployment.

## Summary

**What it is:** Single Go binary (and Docker image) that loads Terraform, CloudFormation, Kubernetes YAML, and preview ARM into OPA. Ships CIS-mapped rule packs and custom Rego.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Pre-merge IaC gate | Fail CI on CIS-style findings before apply |
| Multi-format repos | One scanner across TF, CFN, and k8s manifests |
| Custom Rego already | Reuse OPA skills with Regula's IaC loaders |

**When to skip:**

- You already standardize on **[[Checkov]]** or Conftest with a working pack
- Need deep SaaS policy management rather than a CLI report
- Project activity and rule freshness matter more than feature fit (confirm maintenance before adopt)

**Trade-offs:** Strong OPA alignment and CIS mapping. Fugue-origin OSS; weigh against Checkov's broader IaC coverage and ecosystem before promoting.

## Details

| Topic | Notes |
|-------|--------|
| Inputs | Terraform source/plan, CloudFormation, Kubernetes YAML, ARM (preview) |
| Policy language | Rego via **[[Open Policy Agent]]** |
| Outputs | JSON, JUnit, TAP for CI |
| Pairing | **[[Terraform]]** / **[[Kubernetes]]** repos; GitHub Actions example upstream |

**References**

- [Regula docs](https://regula.dev/)
- [fugue/regula on GitHub](https://github.com/fugue/regula)
