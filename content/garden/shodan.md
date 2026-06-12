---
title: "Shodan"
date: 2026-05-28
lastmod: 2026-06-12
draft: false

keywords:
  - Shodan

params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: "No Change"
aliases:
  - /radar/tools/shodan
---

[Shodan](https://www.shodan.io/) is a search engine for Internet-connected devices and services. It indexes banners, open ports, software versions, and misconfigurations across the public IPv4/IPv6 space. We **adopt** it for authorized attack surface mapping and **[[DevSecOps]]** exposure checks. A paid Membership pays for itself on one or two investigations per month and beats juggling free-tier credits across ad hoc lookups.

## Blurb

> Search Engine for the Internet of Things

## Summary

**What it is:** Continuous crawler plus query UI and API for finding hosts by product, CVE, country, org, certificate, and other facets.

**When to use:** the default external recon index for teams with authorized scope. Validate what attackers can see on your public IPs. Hunt forgotten dev endpoints after M&A. Run threat intel on exposed industrial or IoT gear (with legal clearance).

**When to skip:** Purely internal apps with no Internet footprint. Orgs that forbid third-party recon data. Needs that require active authenticated testing instead of passive index lookup.

**API:** paid plans unlock automated queries, alerts when new hosts match a filter, and integrations into SIEM or SOAR playbooks.

## Personal Experience

The one-time Membership cost is something every DevOps and SecOps should have. While the query and scan credits are low, they are generally more than enough for 1 to 2 investigations per month.

Before many companies stopped bug bounties because of AI slop, the Freelance account and a few high-quality monitors would net a small amount of passive income; certainly enough to justify the cost. These days that income is less reliable, but the Membership remains valuable.

## Details

| Use case | Notes |
|----------|--------|
| **Asset discovery** | Compare Shodan results to CMDB or cloud inventory |
| **CVE exposure** | Search by product version after advisory drops |
| **Monitoring** | Saved searches + alerts when new services appear on your netblocks |
| **Compliance** | Document authorized use; restrict API keys |

**Ethics and policy:** only query assets you own or have written permission to assess; pair external recon with internal **[[Shift Left]]** scanning.

**Alternatives:** **[[Censys]]** and **[[ZoomEye]]** overlap on host lookup. Pick one primary index to avoid alert fatigue.

**References**

- [Shodan](https://www.shodan.io/)
- [Shodan API documentation](https://developer.shodan.io/)
