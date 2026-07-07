---
title: Access on Demand
date: '2025-04-05'
lastmod: '2026-07-02'
draft: false
keywords:
- Access on Demand
params:
  garden:
    kind: item
    usefulness: trial
    category: technique
    movement: No Change
---

[Access on Demand](https://en.wikipedia.org/wiki/Just-in-time_access) replaces standing access with audited, time-bound elevation to sensitive systems. We **trial** it under **[[Technique]]** when SSO can support the workflow.

## Summary

**When to use:** Production or sensitive systems where compliance requires logged reason and duration for privilege elevation, and your IdP supports SAML or OIDC group workflows.

**Implementation pattern:** Grant standing groups plus `aod_<group>` variants. Provide a request UI that logs reason, issues a short-lived session token with the elevated group, and expires access on schedule. Downstream systems authorize on the non-`aod` group names.
