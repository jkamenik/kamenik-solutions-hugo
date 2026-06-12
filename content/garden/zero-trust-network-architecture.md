---
title: "Zero Trust Network Architecture"
date: 2024-10-01
lastmod: 2026-06-12
draft: false

keywords:
  - Zero Trust Network Architecture
  - BeyondCorp
  - zero trust

params:
  aliases:
    - BeyondCorp
    - zero trust
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "No Change"
    subcategories:
      - specification
---

[Zero Trust Network Architecture](https://en.wikipedia.org/wiki/Zero_trust_security_model) (zero trust) assumes **no implicit trust** based on network location. Every access request is authenticated, authorized, and encrypted using identity, device posture, and policy. We **adopt** these principles as the default security posture. Implement access with **[[ZTNA]]**, **[[Access on Demand]]**, and strong **[[Single Sign-on]]**, not perimeter VPNs alone.

## Blurb

> Zero trust security is an information-security model which maintains strict access controls and does not trust anything by default, inside or outside an organization's perimeter.

## Summary

**Core idea:** without a trusted "inside" network, you must enforce safety on every request. Perimeter firewalls and VPNs that grant broad LAN access do not meet that bar.

**Common pillars (NIST-style):**

| Pillar | Practice |
|--------|----------|
| Verify explicitly | AuthN/AuthZ on every request; device and user posture |
| Least privilege | Just enough access for the task; time-bound where possible |
| Assume breach | Segment, log, and monitor; no silent lateral movement |

**How we apply it:** treat **[[ZTNA]]** as the default remote-access pattern. Pair **[[Access on Demand]]** for production and break-glass paths. Use **[[Tailscale]]** or similar L3 VPN only when an app truly needs network adjacency, not as the org-wide front door.

**Not the same as:** **[[ZTNA]]** (product and broker pattern) or a single vendor SKU. This note is the **reference architecture** under **[[Specification]]**.

## Details

- **Origin:** popularized in industry by Google's BeyondCorp papers (see **Garden Notes**). NIST SP 800-207 documents a widely cited zero-trust architecture model.
- **Identity:** **[[Single Sign-on]]** (OIDC/SAML) is the front door; group and role claims feed **[[Policy as Code]]** and access brokers.
- **Products (examples):** **[[Boundary (Hashicorp)]]** for session-brokered infra access; commercial ZTNA suites when you need a managed broker fleet.
- **Contrast:** "castle and moat" VPNs, flat VPC peering, and long-lived SSH keys on bastions are **hold** patterns for new work.
