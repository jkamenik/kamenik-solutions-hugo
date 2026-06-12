---
title: "Azure Policy"
date: 2026-05-28
lastmod: 2026-06-12
draft: false

keywords:
  - Azure Policy

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
aliases:
  - /radar/tools/azure-policy
---

[Azure Policy](https://learn.microsoft.com/en-us/azure/governance/policy/) is Microsoft's service for enforcing and assessing resource compliance at management group, subscription, or resource group scope.

We **assess** it under **[[Tool]]** for estates that already run **[[Azure]]**.

It provides deny, audit, and remediation effects plus regulatory initiatives without **[[Cloud Custodian]]**.

Evaluation can lag minutes. Pilot Audit before wide Deny, especially when **[[Azure]]** is **hold** for greenfield.

## Blurb

> Azure Policy helps you manage and prevent IT issues with policy definitions that enforce rules and effects for your resources.

## Summary

**What it is:** JSON policy definitions and initiatives (policy sets). Assignments at scope, a compliance dashboard, remediation tasks, and Defender for Cloud regulatory views.

**When to use:**

- Azure-primary estates
- Entra-backed org structure
- Tag and location standards
- Built-in regulatory initiatives (NIST, PCI, etc.)
- **[[Policy as Code]]** workflows (Git + CI/CD) for definition lifecycle

**When to skip:**

- Multi-cloud policy in one language (see **[[Cloud Custodian]]** or OPA/Rego)
- Greenfield where **[[Azure]]** is **hold**
- Sub-minute deny at the API edge (Policy evaluation can lag)

**Pairs with:** **[[Policy as Code]]** and IaC gates on PRs. Policy for in-subscription and org-wide assignment. **[[DevSecOps]]** for pipeline plus cloud governance.

## Details

| Topic | Notes |
|-------|--------|
| **Definitions** | Built-in and custom; parameters, conditions, effects (Deny, Audit, DeployIfNotExists, Modify, etc.) |
| **Initiatives** | Grouped policies deployed as one assignment |
| **Scope** | Management group, subscription, or resource group |
| **Kubernetes** | Separate AKS policy add-on and Azure Machine Configuration paths |

**Practices:** Assign at management group for consistency. Use exemptions sparingly and document them. Store custom definitions in **[[git]]** and deploy via pipeline. Pilot Audit before Deny on shared subscriptions.

**References**

- [Azure Policy documentation](https://learn.microsoft.com/en-us/azure/governance/policy/)
- [Overview of Azure Policy](https://learn.microsoft.com/en-us/azure/governance/policy/overview)
