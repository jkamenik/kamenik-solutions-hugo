---
title: Kubescape
date: '2026-05-27'
lastmod: '2026-07-02'
draft: false
keywords:
- Kubescape
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - code-scanner
aliases:
- /radar/tools/kubescape
---

[Kubescape](https://github.com/kubescape/kubescape) is a tool we **assess** in the garden.

## Blurb

> Kubescape is an open-source Kubernetes security platform for your IDE, CI/CD pipelines, and clusters. It includes risk analysis, security, compliance, and misconfiguration scanning, saving Kubernet...

## Summary

**Modes:** CLI scans on manifests; in-cluster operator; CI hooks for **[[Pull Request]]** checks on changed YAML.

**When to use:** need a single CLI for posture reporting across many clusters; evaluating ARMO's control catalog without buying a full CNAPP yet.

**When to skip:** already standardized on another CNAPP or admission policy stack (**[[Policy as Code]]**, OPA Gatekeeper) with overlapping coverage.
