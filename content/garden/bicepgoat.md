---
title: BicepGoat
date: '2026-06-15'
lastmod: '2026-07-01'
draft: false
keywords:
- BicepGoat
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: New
---

[BicepGoat](https://github.com/bridgecrewio/bicepgoat) is Bridgecrew's "Vulnerable by Design" Bicep and ARM template repository for Azure. It deploys intentionally misconfigured resources for IaC security training. We **trial** it as a legal target for **[[Checkov]]** drills on Azure-native **[[IaC]]**. Never deploy it in production subscriptions or beside sensitive workloads.

## Blurb

> BicepGoat is Bridgecrew's "Vulnerable by Design" Bicep and ARM repository. BicepGoat is a learning and training project that demonstrates how common configuration errors can find their way into production cloud environments.

## Summary

BicepGoat sits in Bridgecrew's IaC Goat family alongside **[[TerraGoat]]** (Terraform multi-cloud). Use it when the lab stack is Azure Bicep or ARM, not HCL.

**When to use:** calibrating **[[Checkov]]** on Bicep and ARM files; teaching **[[Policy as Code]]** and **[[DevSecOps]]** gates before Azure deploy; Azure-only teams that will not run **[[TerraGoat]]**'s AWS or GCP modules.

**When to skip:** you cannot isolate a disposable Azure subscription; you need Terraform labs (use **[[TerraGoat]]**); you need app-layer vuln targets only (use **[[DVWA]]** or **[[Juice Shop]]**).

**Scope:** intentionally vulnerable Bicep and ARM templates. Upstream warns that apply creates real insecure Azure resources.

## Details

### Compared to [[TerraGoat]]

| Lens | BicepGoat | [[TerraGoat]] |
|------|-----------|---------------|
| IaC language | Bicep and ARM | Terraform (HCL) |
| Cloud focus | Azure | AWS, Azure, GCP |
| Scanner pairing | **[[Checkov]]** (Bicep/ARM policies) | **[[Checkov]]** (Terraform policies) |
| Best fit | Azure-native IaC training | Multi-cloud Terraform training |

### Deployment Guardrails

- Use a dedicated sandbox subscription with no production data.
- Read upstream warnings before deploy: resources are intentionally insecure.
- Tear down all deployed resources when the lab ends.
- Scan the repo locally with **[[Checkov]]** before any deploy to practice catch-before-deploy.

### Scan-First Lab Sketch

```bash
git clone https://github.com/bridgecrewio/bicepgoat.git
cd bicepgoat
checkov -d .
# Optional: deploy in sandbox only after reviewing findings
```
