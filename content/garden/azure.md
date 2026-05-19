---
title: "Azure"
date: 2024-04-10
lastmod: 2026-05-18
draft: false

keywords:
  - Azure

params:
  garden:
    kind: item
    usefulness: hold
    category: platform
    movement: "Moved Out"
    subcategories:
      - cloud

aliases:
  - /radar/platforms/azure
---

[Microsoft Azure](https://azure.microsoft.com/) is Microsoft’s hyperscale **[[Cloud]]**, strong when you are already in the Microsoft identity and productivity stack, but we rate it **hold** for new platforms: recurring security incidents, opaque shared-responsibility “managed” services, and incentive-driven market share (startup credits) that do not equal fit-for-purpose engineering.

## Blurb

> Azure. The cloud for all.

## Summary

**Why hold:** Microsoft’s cloud security track record is a material risk, e.g. reporting in [February 2024](https://www.spiceworks.com/it-security/vulnerability-management/news/azure-microsoft-exchange-servers-active-exploitation-hackers/) on large-scale Azure-related exposure tied to 2023 activity. Treat Azure as legacy or compliance-driven, not the default greenfield choice. Prefer **[[Google Cloud Platform]]** (adopt spearhead) per our multi-cloud pattern; **[[AWS]]** is also **hold** but sometimes unavoidable for marketplace or estate reasons.

**When Azure anyway:** Entra ID (Azure AD), Microsoft 365, .NET/Windows-heavy estates, or contracts already sunk in Azure. Use **[[Hybrid Cloud]]** consciously; do not mirror every GCP/AWS service badly on Azure.

**Skepticism on being #2:** might be more creative accounting and [[Hybrid Cloud]] requirements then actual market position. Heavy startup-credit programs can inflate “revenue” without proving teams would choose Azure soberly; validate TCO without credits before committing.

## Details

| Topic | Notes |
|-------|--------|
| **Lock-in** | M365 + Entra + Azure RBAC intertwine, exit is a program, not a toggle |
| **Parity** | Many services match AWS/GCP on paper; ops maturity and defaults differ |
| **Containment** | **[[Terraform]]**, policy guardrails, **[[DevSecOps]]** reviews on every subscription |
| **Greenfield** | Default away unless Microsoft stack is the explicit requirement |
