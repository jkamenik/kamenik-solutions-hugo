---
title: "kube-bench"
date: 2026-05-27
lastmod: 2026-05-27
draft: false

keywords:
  - kube-bench

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - code-scanner

aliases:
  - /radar/tools/kube-bench
---

[kube-bench](https://github.com/aquasecurity/kube-bench) runs CIS Kubernetes Benchmark checks against the control plane and nodes. It reports pass/fail per hardening recommendation. We **assess** it alongside **[[Kubescape]]** before picking a standard cluster compliance scanner.

## Blurb

> kube-bench is a Go application that checks whether Kubernetes is deployed securely by running the checks documented in the CIS Kubernetes Benchmark.

## Summary

| Lens | kube-bench | [[Kubescape]] |
|------|------------|---------------|
| Focus | CIS benchmark sections per K8s version | Broader frameworks (NSA, MITRE, signed controls) |
| Run model | Job on node or master; JSON reports | CLI, operator, CI on manifests |
| Best fit | CIS audit evidence for regulated K8s | Multi-framework posture and PR checks |

**When to use:** auditors ask for CIS-aligned evidence; you need a well-known benchmark mapping per K8s minor version.

**When to skip:** only application-level security matters; already standardized on Kubescape with overlapping CIS coverage.
