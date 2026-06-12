---
title: "First Touch Provisioning"
date: 2026-01-10
lastmod: 2026-06-12
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
    movement: "No Change"
aliases:
  - /radar/techniques/first-touch-provisioning
---

[First Touch Provisioning](https://en.wikipedia.org/wiki/Provisioning)

**First touch provisioning** creates the **foundation layer** of infrastructure: cloud accounts and guardrails, networks, DNS, IAM roles, clusters, VMs, databases as managed services, and remote state. We **adopt** it via **[[Declarative IaC]]** (**[[Terraform]]** / OpenTofu). **[[second touch provisioning]]** configures what runs *on* that foundation (packages, agents, app config); prefer immutable images and **[[GitOps]]** over repeated SSH configuration.

## Blurb

> In computing, provisioning means to provide or equip an information technology system with products or services required to make it operational.

## Summary

**First touch (typical artifacts):**

| Layer | Examples |
|-------|----------|
| **Identity / org** | AWS accounts, GCP projects, Azure subscriptions, org policies |
| **Network** | VPC/VNet, subnets, firewalls, load balancers, private DNS |
| **Compute platform** | EKS/GKE/AKS cluster, autoscaling groups, serverless runtimes |
| **Data plane (managed)** | RDS, Cloud SQL, S3/GCS buckets with policies |
| **Ops plumbing** | Remote state buckets, CI OIDC roles, observability sinks |

**Second touch (separate technique, often assess):**

- **[[Ansible]]** playbooks on existing VMs
- `cloud-init` / startup scripts that drift from IaC
- In-cluster **[[Helm]]** / manifests after the cluster exists

**When first touch is enough:**

- **[[Kubernetes]]**: cluster + IAM + networking in Terraform; workloads via GitOps
- **Serverless**: functions, queues, tables defined declaratively; no SSH config loop
- **[[Cattle Not Pets]]**: golden images built in CI, not hand-provisioned servers

**When you need both touches:**

- Brownfield VMs imported into the cloud
- Legacy middleware Ansible still owns until replaced by containers
- Split responsibility: platform team owns first touch, app team owns Helm/GitOps (still two phases, different owners)

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
