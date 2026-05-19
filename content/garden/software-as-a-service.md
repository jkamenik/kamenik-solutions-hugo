---
title: "Software as a Service"
date: 2024-10-01
lastmod: 2026-05-18
draft: false

keywords:
  - Software as a Service
  - SaaS

params:
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: "No Change"

aliases:
  - /radar/techniques/saas
---

[Software as a Service](https://en.wikipedia.org/wiki/Software_as_a_service)

**Software as a Service (SaaS)** means the vendor runs the software; customers use it over the network on a subscription or consumption model. We rate the **delivery model** **assess**: powerful for product velocity and ops efficiency, but not every problem should be SaaS, security boundary, tenancy, compliance, and customer data residency must drive the decision.

## Blurb

> Software as a service is a software licensing and delivery model in which software is licensed on a subscription basis and is centrally hosted.

## Summary

**When SaaS fits:** multi-tenant products, frequent releases, **[[Continuous Deployment]]**, per-tenant **[[Feature Flags]]**, and teams that can live by **[[12 Factor App]]** / **[[Cattle Not Pets]]** assumptions (stateless app tiers, managed data stores).

**When to hesitate:** regulated data on shared infrastructure, air-gapped customers, heavy customization per tenant, or “SaaS” as an excuse to skip **[[DevSecOps]]** (shared responsibility is still yours).

**B2B SaaS stack:** identity (**[[Auth0]]**, **[[FrontEgg]]**), observability (**[[OpenTelemetry]]**), and GitOps delivery (**[[ArgoCD]]**) are common companions; each has its own garden rating.

## Details

| Topic | Notes |
|-------|--------|
| **Tenancy** | Single-tenant vs multi-tenant affects cost, isolation, and compliance story |
| **Security** | You own app-layer controls; vendor owns platform; map both in contracts and architecture |
| **Delivery** | Prefer **[[Continuous Deployment]]** over manual releases when uptime SLAs allow |
| **Naming** | Also referenced as **SaaS** throughout the garden |
