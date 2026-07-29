---
title: Stern
date: '2024-10-01'
lastmod: '2026-07-29'
draft: false
keywords:
- Stern
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
---

[Stern](https://github.com/stern/stern) tails logs across multiple pods and containers in **[[Kubernetes]]** with label and regex selectors. We **assess** it as a CLI companion when `kubectl logs` on one pod is not enough.

## Blurb

> Multi pod and container log tailing for Kubernetes.

## Summary

**What it is:** Friendly fork of the original wercker/stern. Streams combined logs from matching pods; useful during rollouts and multi-replica debugging.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Multi-replica debug | Follow all pods for a Deployment or label set |
| Init / sidecar noise | Filter containers while keeping one stream |
| Ad-hoc cluster ops | Faster than scripting `kubectl logs -f` loops |

**When to skip:**

- Centralized logging already answers the question (Loki, Datadog, CloudWatch)
- Need historical search, not live tail
- Cluster policy blocks broad log access from workstations

**Trade-offs:** Great for live incident and deploy watching. Does not replace a log backend. Prefer the `stern/stern` fork over the archived wercker repo.

## Details

| Topic | Notes |
|-------|--------|
| Upstream | Active fork: [stern/stern](https://github.com/stern/stern) |
| Legacy URL | Older notes pointed at wercker/stern |
| Pairing | Local kubeconfig; same RBAC as `kubectl logs` |

**References**

- [stern/stern](https://github.com/stern/stern)
