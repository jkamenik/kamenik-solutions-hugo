---
title: Checkov
date: '2026-06-15'
lastmod: '2026-07-02'
draft: false
keywords:
- Checkov
params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: No Change
    subcategories:
    - code-scanner
---

[Checkov](https://github.com/bridgecrewio/checkov). We **adopt** it under **[[Tool]]** in the garden.

## Blurb

> Prevent cloud misconfigurations and find vulnerabilities during build-time in infrastructure as code, container images and open source packages with Checkov by Bridgecrew. - bridgecrewio/checkov

## Summary

**Role:** CLI and CI gate that scans Terraform, CloudFormation, Kubernetes, Helm, Dockerfile, GitHub Actions, and other IaC or pipeline files before deploy. Graph-based scanning adds context across resources. Output formats include JSON, JUnit, **[[SARIF]]**, and CycloneDX.

| Lens | Checkov | [[Conftest]] | [[Regula]] |
|------|---------|--------------|------------|
| Policy model | Built-in + custom Python/YAML | Rego (OPA) | Built-in Rego bundles |
| Surfaces | IaC, CI workflows, SCA/CVEs | Structured config via OPA | IaC focus (AWS/Azure/GCP/K8s) |
| Best fit | Default IaC and CI PR gate | Cross-stack custom governance | Terraform-centric Rego without OPA ops |

**When to use (default):** any repo with **[[IaC]]** or CI workflow files; CIS, SOC2, or cloud-provider hardening on every **[[Pull Request]]**; teams want local scans that match Bridgecrew or Prisma Cloud policy packs.

**When to skip:** policy logic must live in OPA and run at admission time (**[[Policy as Code]]** + **[[Conftest]]**); only application source linting matters; **[[Regula]]** already covers the full IaC stack with less policy maintenance.

**Pairs with:** `terraform plan` JSON scanning, pre-commit hooks, **[[GitHub Actions]]** or Jenkins gates, Prisma Cloud for centralized policy management.

## Details

| Topic | Notes |
|-------|--------|
| **Install** | `pip install checkov` (Python 3.9-3.12); Docker image `bridgecrew/checkov` |
| **IaC inputs** | Terraform, Terraform plan/JSON, CloudFormation, SAM, Bicep, ARM, OpenTofu, Ansible, Serverless |
| **K8s inputs** | Kubernetes manifests, Helm charts (rendered), Kustomize |
| **CI inputs** | GitHub Actions, GitLab CI, Azure Pipelines, CircleCI, Bitbucket Pipelines, Argo Workflows |
| **SCA** | Open source package and image CVE scanning (separate from IaC checks) |
| **Custom policies** | Python attribute policies; YAML attribute and composite policies |
| **Suppressions** | Inline skip comments and CLI global skips for accepted risk |
| **Upstream** | Open source by Bridgecrew; maintained under Prisma Cloud |

**References**

- [Checkov documentation](https://www.checkov.io/1.Welcome/What%20is%20Checkov.html)
- [GitHub repository](https://github.com/bridgecrewio/checkov)
- [Policy index](https://github.com/bridgecrewio/checkov/blob/main/docs/5.Policy%20Index/all.md)
