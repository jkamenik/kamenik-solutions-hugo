---
title: "Clutch"
date: 2026-05-27
lastmod: 2026-05-27
draft: false

keywords:
  - Clutch

params:
  garden:
    kind: item
    usefulness: hold
    category: platform
    movement: "No Change"
aliases:
  - /radar/platforms/clutch
---

[Clutch](https://clutch.sh/) is Lyft's extensible platform for infrastructure operations. It exposes workflows (resizing databases, rerouting traffic, running jobs) through a UI and API with pluggable components. We **hold** it: Lyft [archived the repo](https://github.com/lyft/clutch) on **2026-02-13** and no longer accepts issues, pull requests, or new features. Treat it as a reference for **[[Internal Developer Platform]]** patterns, not as a platform to adopt or extend.

## Blurb

> Clutch is an extensible platform for infrastructure tooling.

## Summary

**Architecture:** backend services plus protobuf-defined workflows; frontend for operators; auth integrations for enterprise SSO.

**When to use:** studying how a large org wrapped risky ops in audited workflows; reading source as a pattern library before building an in-house IDP.

**When to skip:** net-new deployments; teams expecting upstream fixes, security patches, or community support. Fork only if you can own long-term maintenance.

**Upstream:** [github.com/lyft/clutch](https://github.com/lyft/clutch) (archived, read-only).

## Details

Lyft posted an archival notice on the GitHub README before marking the repository read-only. Existing code and docs remain available for reference. Contact for questions was listed as `clutch@lyft.com` in the notice.

| Topic | Notes |
|-------|--------|
| Status | Archived **2026-02-13**; no new development |
| License | Apache-2.0 (fork-friendly, but maintenance burden is on you) |
| Garden stance | **hold** - reference only, not adopt |
