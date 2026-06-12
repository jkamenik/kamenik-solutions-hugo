---
title: "Censys"
date: 2026-05-28
lastmod: 2026-06-12
draft: false

keywords:
  - Censys

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
aliases:
  - /radar/tools/censys
---

[Censys](https://censys.com/) is an Internet intelligence platform built on continuous global scanning, certificate observation, and structured host data. We **assess** it for authorized attack surface mapping and **[[DevSecOps]]** exposure checks. It complements passive recon indexes like **[[Shodan]]** when you need certificate pivots, enterprise ASM, or threat-infrastructure context.

## Blurb

> The Authority for Internet Intelligence and Insights

## Summary

**What it is:** Censys maintains the Internet Map, a continuously updated view of hosts, services, certificates, and software fingerprints. Censys Search supports ad hoc lookups. Censys Platform adds Attack Surface Management, adversary investigation, and API access for SOC workflows.

**When to use:** Compare external visibility to CMDB or cloud inventory. Pivot on X.509 certificates and related hosts. Monitor org-owned netblocks for new exposures. Hunt threat actor infrastructure with structured threat data (enterprise tiers).

**When to skip:** Purely internal apps with no Internet footprint. Orgs that forbid third-party recon data. Teams that have already standardized on one index and want to avoid duplicate alerts. Needs that require active authenticated testing instead of passive lookup.

**API:** platform and search APIs support automation, collections, and integrations. Pricing is enterprise-oriented compared with hobby-tier **[[Shodan]]** memberships.

## Details

| Use case | Notes |
|----------|--------|
| **Asset discovery** | Find shadow IT and forgotten subdomains tied to your org |
| **Certificate research** | Search one of the largest public X.509 corpora for related infrastructure |
| **CVE exposure** | Fingerprint services and tie them to CVE context |
| **ASM** | Continuous monitoring with risk prioritization (Platform SKU) |
| **Threat hunting** | Adversary Investigation module links malware and actor data to hosts |

**Not the same as:** [Censys Technologies](https://censystech.com/) (BVLOS drones and aerial analytics). The security vendor lives at censys.com.

**Ethics and policy:** only query assets you own or have written permission to assess. Pair external recon with internal **[[Shift Left]]** scanning.

**Alternatives:** **[[Shodan]]** and **[[ZoomEye]]** overlap on host lookup. Pick one primary index to avoid alert fatigue. Use Censys when certificate depth or enterprise ASM matters more than IoT banner breadth.

**References**

- [Censys](https://censys.com/)
- [Censys Search](https://censys.com/product/censys-search/)
- [Censys documentation](https://docs.censys.com/)
