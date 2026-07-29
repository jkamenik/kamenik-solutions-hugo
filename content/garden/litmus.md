---
title: Litmus
date: '2024-10-01'
lastmod: '2026-07-29'
draft: false
keywords:
- Litmus
- LitmusChaos
params:
  aliases:
  - LitmusChaos
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - chaos-tools
---

[Litmus](https://litmuschaos.io/) (LitmusChaos) is a cloud-native chaos engineering platform for **[[Kubernetes]]**. Teams inject controlled faults to find weaknesses before they cause outages. We **assess** it under **[[Chaos Tools]]** for resilience testing.

## Blurb

> Litmus is a CNCF-hosted, open-source Chaos Engineering platform that helps teams identify infrastructure weaknesses through safe, controlled chaos tests, simple for developers and SREs, built on modern practices, and powered by the community.

## Summary

**What it is:** Kubernetes-native chaos engineering platform. Experiments are defined as custom resources and shared through ChaosHub, a central catalog of reusable fault injections.

**When to use:** You run workloads on Kubernetes and want to validate resilience with repeatable, controlled fault injection. Good fit for **[[SRE]]** practices and pre-production reliability testing.

**When to skip:** You are not on Kubernetes, or chaos experiments are premature because basic observability and recovery paths are not yet in place.

**Status:** CNCF Incubating project (since January 2022), Apache 2.0, actively maintained with a steady monthly release cadence.

## Details

| Topic | Notes |
|-------|--------|
| **Model** | `ChaosExperiment` CRs on Kubernetes; ChaosCenter UI orchestrates runs |
| **ChaosHub** | Central hub of shared, reusable chaos experiments at hub.litmuschaos.io |
| **Governance** | CNCF Incubating; broad multi-org contributor base |

**References**

- [LitmusChaos site](https://litmuschaos.io/)
- [litmuschaos/litmus on GitHub](https://github.com/litmuschaos/litmus)
- [Litmus on CNCF](https://www.cncf.io/projects/litmus/)
