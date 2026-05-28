---
title: "Kubescape"
date: 2026-05-27
lastmod: 2026-05-27
draft: false

keywords:
  - Kubescape

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - code-scanner

aliases:
  - /radar/tools/kubescape
---

[Kubescape](https://github.com/kubescape/kubescape) is an open source Kubernetes security scanner. It checks clusters and manifests against NSA/CISA guidance, MITRE ATT&CK, and signed controls frameworks. We **assess** it next to kube-bench-style tools before standardizing a cluster compliance gate.

## Blurb

> Kubescape is an open-source Kubernetes security platform.

## Summary

**Modes:** CLI scans on manifests; in-cluster operator; CI hooks for **[[Pull Request]]** checks on changed YAML.

**When to use:** need a single CLI for posture reporting across many clusters; evaluating ARMO's control catalog without buying a full CNAPP yet.

**When to skip:** already standardized on another CNAPP or admission policy stack (**[[Policy as Code]]**, OPA Gatekeeper) with overlapping coverage.
