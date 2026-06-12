---
title: "Declarative IaC"
date: 2025-01-05
lastmod: 2026-06-12
draft: false

keywords:
  - Declarative IaC

params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "No Change"
aliases:
  - /radar/techniques/declarative-iac
---

[Declarative infrastructure as code](https://en.wikipedia.org/wiki/Infrastructure_as_code) describes **desired end state** in versioned files; a planner/reconciler (Terraform, the Kubernetes API, GitOps controllers) computes and applies the diff. We **adopt** declarative IaC for cloud and cluster shape; **hold** **[[Imperative IaC]]**, **[[CDKs]]**, and **[[Pulumi]]** for new work when a declarative path exists.

## Blurb

> Infrastructure as code is the process of managing and provisioning computer data center resources through machine-readable definition files, rather than physical hardware configuration or interactive configuration tools.

## Summary

**Declarative vs imperative (IaC):**

| Style | Artifact | Garden stance |
|-------|----------|---------------|
| **Declarative IaC** | Desired state (HCL, YAML, JSON) | **adopt** |
| **[[Imperative IaC]]** | Programs that emit or call APIs | **hold** |

**Why adopt:** reviewers see **what** should exist; engines handle ordering and drift detection. Pairs with **[[GitOps]]** (PR-driven apply), **[[Policy as Code]]** (lint before merge), and **[[Shift Left]]** / **[[DevSecOps]]**.

**Common tools (declarative lane):**

| Surface | Examples |
|---------|----------|
| Cloud accounts | **[[Terraform]]** / OpenTofu (**[[HCL]]**) |
| Kubernetes | manifests, **[[Helm]]** charts (**[[YAML]]**) |
| Cluster delivery | **[[ArgoCD]]** reconciles Git desired state |
| Host config (when needed) | **[[Ansible]]** playbooks (prefer images + declarative cloud where possible) |

**DRY without going imperative:** modules, variables, `for_each`, Helm subcharts, and policy bundles. Repetition is a design smell, not a reason to generate IaC from TypeScript.

**When imperative is still OK:** application code, one-off scripts, and glue. The garden **hold** is scoped to **infrastructure generators**, not all programming.

## Details

| Topic | Notes |
|-------|--------|
| **Reconciliation** | Plan/apply or controller loop; fix drift instead of documenting it |
| **Blast radius** | Declarative plans show resource graph changes; imperative generators hide side effects |
| **State** | Remote state (Terraform) or etcd (K8s); back up and lock |
| **Secrets** | Never in Git; use secret managers and external data sources |
| **Legacy import** | `terraformer` and similar can bootstrap; then refactor into modules |

**References**

- [Wikipedia: Infrastructure as code](https://en.wikipedia.org/wiki/Infrastructure_as_code)
