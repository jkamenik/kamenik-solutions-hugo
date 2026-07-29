---
title: First Touch Provisioning
date: '2026-01-10'
lastmod: '2026-07-29'
draft: false
keywords:
- First Touch Provisioning
- first-touch provisioning
params:
  aliases:
  - first-touch provisioning
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
aliases:
- /radar/techniques/first-touch-provisioning
---

[First Touch Provisioning](https://en.wikipedia.org/wiki/Provisioning). **First touch provisioning** creates the **foundation layer** of infrastructure: cloud accounts and guardrails, networks, DNS, IAM roles, clusters, VMs, databases as managed services, and remote state.

## Summary

**Garden stance:** We **adopt** First Touch Provisioning for our estate.

**Key points:**

| Topic | Notes |
|-------|--------|
| **Tools** | **[[Terraform]]** (**adopt**); avoid new **[[Imperative IaC]]** / **[[Pulumi]]** generators for greenfield |
| **State** | Remote backend per env; locking; no local-only state for shared infra |
| **Modules** | Reusable VPC/cluster modules; watch blast radius (**[[DRY]]** discipline) |
| **Policy** | **[[Policy as Code]]** on plans before apply |
| **Provisioner anti-pattern** | Terraform `remote-exec` / heavy `local-exec` blurs touches; keep first touch declarative |

**References**

- [Wikipedia: Provisioning](https://en.wikipedia.org/wiki/Provisioning)

## Details

| Topic | Notes |
|-------|--------|
| **Tools** | **[[Terraform]]** (**adopt**); avoid new **[[Imperative IaC]]** / **[[Pulumi]]** generators for greenfield |
| **State** | Remote backend per env; locking; no local-only state for shared infra |
| **Modules** | Reusable VPC/cluster modules; watch blast radius (**[[DRY]]** discipline) |
| **Policy** | **[[Policy as Code]]** on plans before apply |
| **Provisioner anti-pattern** | Terraform `remote-exec` / heavy `local-exec` blurs touches; keep first touch declarative |

**References**

- [Wikipedia: Provisioning](https://en.wikipedia.org/wiki/Provisioning)
