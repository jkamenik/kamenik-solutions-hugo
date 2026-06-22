---
title: "AWS Config"
date: 2026-05-28
lastmod: 2026-06-22
draft: false

keywords:
  - AWS Config

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
aliases:
  - /radar/tools/aws-config
---

[AWS Config](https://aws.amazon.com/config/) is AWS's managed service for resource inventory, configuration history, and continuous compliance evaluation.

We **assess** it under **[[Tool]]** for estates that already run **[[AWS]]**.

It fits native rules, conformance packs, and multi-account aggregators without **[[Cloud Custodian]]**.

Prefer **[[Cloud Custodian]]** or **[[Policy as Code]]** when you need one policy language across clouds.

## Blurb

> AWS Config is a service that enables you to assess, audit, and evaluate the configurations of your AWS resources.

## Summary

**What it is:** Continuous recording of resource configuration changes. AWS Config rules (managed and custom). Conformance packs, multi-account aggregators, and optional remediation (SSM Automation or Lambda).

**When to use:**

- AWS-only or AWS-primary estates
- Regulatory audit trails
- Org-wide guardrails via AWS Organizations
- Teams that want native compliance dashboards without c7n or OPA on the control plane

**When to skip:**

- Multi-cloud policy in one language (see **[[Cloud Custodian]]** or **[[Conftest]]** on IaC)
- High churn where rule evaluations and configuration items drive cost
- Greenfield where **[[AWS]]** is **hold** and another cloud is viable

**Pairs with:** **[[Policy as Code]]** on PRs. Config for post-deploy drift and inventory. **[[DevSecOps]]** to gate merges while Config watches live accounts.


## Details

| Topic | Notes |
|-------|--------|
| **Rules** | Managed rules, custom rules, conformance packs (bundled rules + remediation) |
| **Aggregation** | Central compliance view across accounts and Regions |
| **Remediation** | Manual or automatic; SSM documents or custom Lambda |
| **Notifications** | SNS on non-compliance and configuration changes |

**Practices:** Start with detective rules (notify, dashboard) before auto-remediate. Scope recording to resource types you need. Use aggregators so security teams see compliance without console access to every account.

**References**

- [What is AWS Config?](https://docs.aws.amazon.com/config/latest/developerguide/WhatIsConfig.html)
- [AWS Config product page](https://aws.amazon.com/config/)
