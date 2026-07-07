---
title: IaC
date: '2023-12-01'
lastmod: '2026-07-07'
draft: false
keywords:
- IaC
params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
---

[Infrastructure as code (IaC)](https://en.wikipedia.org/wiki/Infrastructure_as_code) manages and provisions environments through versioned, machine-readable definitions instead of manual console changes. We **adopt** it as the foundation for **[[Shift Left]]**, **[[DevSecOps]]**, and **[[GitOps]]** delivery.

## Blurb

> Infrastructure as code (IaC), also known as software-defined infrastructure (SDI), is the process of managing and provisioning computer data centers through machine-readable definition files, rather than physical hardware configuration or interactive configuration tools.

## Summary

**When to use:**

| Use | Notes |
|-----|--------|
| **Repeatable environments** | Dev, staging, and prod share the same definitions with parameter differences |
| **Reviewable change** | PRs show diffs before apply; auditors get Git history |
| **Drift control** | Reconcilers detect and correct config that drifted from declared state |
| **Security gates** | Pair with **[[Policy as Code]]** scanners on every PR |

**When to skip:**

- Ephemeral sandboxes you tear down in hours and never reproduce
- One-off experiments where a console click is faster than codifying
- Teams with no Git or PR culture yet (fix process before scaling IaC)

**Garden split:** **[[Declarative IaC]]** (**adopt**) for desired-state files; **[[Imperative IaC]]** (**hold**) for generators that hide side effects. See child notes for tool tables and anti-patterns.

**Related practices:** **[[GitOps]]** applies IaC through merge workflows. **[[Shift Left]]** and **[[DevSecOps]]** expect infra changes in the same pipeline as application code.

## Details

### Declarative vs Imperative

| Style | Artifact | Garden stance |
|-------|----------|---------------|
| **[[Declarative IaC]]** | Desired end state (HCL, YAML, JSON) | **adopt** |
| **[[Imperative IaC]]** | Programs that call cloud APIs | **hold** |

Declarative IaC lets reviewers see **what** should exist. Engines compute diffs and handle ordering. Imperative generators can be smaller but make blast radius harder to predict.

### Common Surfaces

| Surface | Examples |
|---------|----------|
| Cloud accounts | **[[Terraform]]** / OpenTofu |
| Kubernetes | manifests, **[[Helm]]** charts |
| Cluster delivery | **[[GitOps]]** controllers reconcile Git state |
| Policy | **[[Policy as Code]]** lint before merge |

### Operating Discipline

| Topic | Notes |
|-------|--------|
| **State** | Remote backends or cluster etcd; lock and back up |
| **Secrets** | Never in Git; use secret managers and external data sources |
| **Modules** | DRY through modules and variables, not imperative codegen |
| **Import** | Bootstrap tools like terraformer can help; refactor into modules after |

**References**

- [Wikipedia: Infrastructure as code](https://en.wikipedia.org/wiki/Infrastructure_as_code)
- **[[Declarative IaC]]** for expanded tool matrix and reconciliation notes
