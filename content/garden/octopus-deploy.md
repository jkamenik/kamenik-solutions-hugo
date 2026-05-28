---
title: "Octopus Deploy"
date: 2026-05-27
lastmod: 2026-05-27
draft: false

keywords:
  - Octopus Deploy

params:
  garden:
    kind: item
    usefulness: assess
    category: platform
    movement: "New"
    subcategories:
      - ci-cd-tools

aliases:
  - /radar/platforms/octopus-deploy
---

[Octopus Deploy](https://octopus.com/) is a deployment automation platform for releases to IIS, Windows services, **[[Kubernetes]]**, and cloud targets. It separates build (CI) from release orchestration with tenants, channels, and runbooks. We **assess** it for .NET and multi-target promotion flows; **[[GitOps]]** or Actions-native deploy is the default elsewhere.

## Blurb

> Octopus Deploy is a deployment automation and release management tool that helps teams ship software to production.

## Summary

**When to use:** Octopus is already the system of record for releases; need guided deployments with approvals and audit trails across heterogeneous targets.

**When to skip:** container-only shops on **[[ArgoCD]]**; teams that want all deploy logic in git with no external release server.

**Note:** Reminder title was "Octopus CD"; product name is Octopus Deploy.
