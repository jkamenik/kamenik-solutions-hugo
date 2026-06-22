---
title: "Kuberhealthy"
date: 2026-05-28
lastmod: 2026-06-22
draft: false

keywords:
  - Kuberhealthy

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - monitoring
aliases:
  - /radar/tools/kuberhealthy
---

[Kuberhealthy](https://github.com/kuberhealthy/kuberhealthy) is a **[[Kubernetes]]** operator for synthetic monitoring and continuous process verification. It runs checker pods on a schedule, exposes JSON status, and emits Prometheus metrics. We **assess** it for cluster and app health signals beyond static compliance scans like **[[kube-bench]]** or **[[Kubescape]]**.

## Blurb

> Kuberhealthy is a Kubernetes operator for synthetic monitoring and continuous process verification.

## Summary

**What it does:** Admins define `KuberhealthyCheck` custom resources; the operator schedules checker containers (built-in or custom) that prove APIs, DNS, storage, or cluster mechanics still work.

**When to use:** you want proactive "can we still schedule a pod?" checks; custom HTTP/TCP probes packaged as containers; Prometheus alerting on synthetic failure rates.

**When to skip:** external SaaS synthetics already cover user journeys; tiny clusters where CronJob scripts are enough; rewrite churn on `main` is a concern (upstream notes active rewrite).

**Built-in checks:** daemonset deployment, DNS, storage, and other registry entries documented upstream; write checks in any language as container images.


## Details

| Surface | Purpose |
|---------|---------|
| **Status page** | JSON aggregate of check pass/fail |
| **`/metrics`** | Prometheus scrape endpoint |
| **InfluxDB** | Optional metric forwarding |
| **Helm / YAML** | Install on Kubernetes 1.16+ |

**Versus kube-bench / Kubescape:** those tools audit configuration; Kuberhealthy exercises live behavior on a timer.

**Practices:** keep check runtime short; isolate check RBAC; alert on consecutive failures, not single blips; version-pin checker images.

**References**

- [Kuberhealthy README](https://github.com/kuberhealthy/kuberhealthy)
- [Check creation guide](https://github.com/kuberhealthy/kuberhealthy/blob/master/docs/CHECK_CREATION.md)
