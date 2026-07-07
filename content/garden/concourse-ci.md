---
title: Concourse CI
date: '2026-05-27'
lastmod: '2026-07-02'
draft: false
keywords:
- Concourse CI
params:
  garden:
    kind: item
    usefulness: assess
    category: platform
    movement: No Change
    subcategories:
    - ci-cd-tools
aliases:
- /radar/platforms/concourse-ci
---

[Concourse CI](https://concourse-ci.org/). Is an open source CI system built around pipelines as code, immutable container builds, and the "resources / jobs / tasks" model.

## Summary

**Model:** `fly` CLI sets pipelines from YAML; workers run steps in containers; resources poll git, S3, and other endpoints for new versions.

**When to use:** air-gapped or self-hosted CI with strong isolation; teams already running Concourse at scale with dedicated platform engineers.

**When to skip:** managed SaaS preference; need rich marketplace actions (Actions wins); small teams without ops capacity to run the Concourse cluster.
