---
title: AWS Config
date: '2026-05-28'
lastmod: '2026-07-02'
draft: false
keywords:
- AWS Config
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
aliases:
- /radar/tools/aws-config
---

[AWS Config](https://aws.amazon.com/config/). Is AWS's managed service for resource inventory, configuration history, and continuous compliance evaluation.

## Blurb

> AWS Config is a config tool that helps you assess, audit, and evaluate the configurations and relationships of your resources.

## Summary

**Garden stance:** We **assess** AWS Config for our estate.

**Overview:** We **assess** it under **[[Tool]]** for estates that already run **[[AWS]]**.

**Detail 1:** It fits native rules, conformance packs, and multi-account aggregators without **[[Cloud Custodian]]**.

**Detail 2:** Prefer **[[Cloud Custodian]]** or **[[Policy as Code]]** when you need one policy language across clouds.

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
