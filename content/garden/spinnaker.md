---
title: Spinnaker
date: '2026-05-27'
lastmod: '2026-07-02'
draft: false
keywords:
- Spinnaker
params:
  garden:
    kind: item
    usefulness: assess
    category: platform
    movement: No Change
    subcategories:
    - ci-cd-tools
aliases:
- /radar/platforms/spinnaker
---

[Spinnaker](https://spinnaker.io/). Is an open source multi-cloud continuous delivery platform.

## Summary

**Strengths:** mature deployment strategies (red/black, canary); broad provider support; strong fit when teams already invested in Spinnaker ops.

**Weaknesses:** heavy operational footprint (multiple microservices); steep learning curve; many orgs now prefer Git-declared desired state plus **[[ArgoCD]]** or managed CD.

**When to use:** existing Spinnaker estate; complex multi-account AWS/GCP promotion with battle-tested runbooks.

**When to skip:** new platforms; small teams; Kubernetes-only shops that can standardize on Argo CD or **[[GitHub Actions]]** deploy workflows.
