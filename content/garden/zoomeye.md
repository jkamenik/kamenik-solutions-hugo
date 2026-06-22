---
title: "ZoomEye"
date: 2026-05-28
lastmod: 2026-06-22
draft: false

keywords:
  - ZoomEye

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
aliases:
  - /radar/tools/zoomeye
---

[ZoomEye](https://www.zoomeye.org/) is a cyberspace search engine from Knownsec's 404 Team. It indexes IPv4/IPv6 hosts, web assets, banners, and fingerprints. Coverage is strong in China and broader Asian networks. We **assess** it as a regional complement to **[[Shodan]]** and **[[Censys]]** for authorized **[[DevSecOps]]** recon. It is not our sole primary index.

## Blurb

> ZoomEye is a cyberspace search engine that allows users to search for network devices through a browser.

## Summary

**What it is:** Continuous Internet scanner plus search UI, API, and official Python SDK (`ZoomEye-python`). Supports host (`v4`/`v6`) and web search modes, dork-style filters, facets, and exports.

**When to use:**

- Fill gaps that Western indexes miss in Chinese or Asian IP space
- Compare results across engines after M&A or cloud expansion into APAC
- Integrate via API or CLI in authorized pipelines
- Pair with tools like Nuclei that support ZoomEye as an uncover engine

**When to skip:** Teams that have already standardized on one Western index. Investigations where query logging under Chinese jurisdiction is unacceptable OPSEC. Needs already covered entirely by **[[Shodan]]** without APAC-specific gaps. Orgs that forbid third-party recon data.

**API:** freemium web tier with tight daily search limits on free accounts. Paid plans and API keys unlock programmatic search, larger page sizes, and automation.


## Details

| Use case | Notes |
|----------|--------|
| **Regional asset discovery** | `country:"CN"` and related filters for APAC exposure |
| **Service hunting** | `port:`, `app:`, `service:`, `device:` dorks |
| **Web exposure** | `sub_type:web` for crawled sites and components |
| **Version/CVE context** | `ver:` and product filters after advisories drop |
| **Automation** | Official SDK, CLI, and third-party wrappers |

**Data sovereignty:** Knownsec operates ZoomEye in China. Queries are logged. Treat sensitive hunts accordingly.

**Ethics and policy:** only query assets you own or have written permission to assess. Pair external recon with internal **[[Shift Left]]** scanning.

**Alternatives:** **[[Shodan]]** remains our default global index. **[[Censys]]** leads on certificate pivots and enterprise ASM. Use ZoomEye when APAC coverage or a second opinion matters.

**References**

- [ZoomEye](https://www.zoomeye.org/)
- [ZoomEye documentation](https://www.zoomeye.org/doc/)
- [ZoomEye-python SDK](https://github.com/zoomeye/SDK)
