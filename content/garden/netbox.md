---
title: Netbox
date: '2024-10-01'
lastmod: '2026-07-28'
draft: false
keywords:
- Netbox
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
---

[NetBox](https://docs.netbox.dev/en/stable/) is an open-source network source of truth for IPAM, DCIM, and automation APIs. We **assess** it for on-premises and data-center estates, where provider-native **[[Cloud]]** inventory does not already cover the need.

## Blurb

> The cornerstone of every automated network

## Summary

**When to use:** You need an intended-state model for sites, racks, devices, cables, prefixes, VLANs, and VRFs. Pair it with **[[Ansible]]**, **[[Terraform]]**, or other controllers that consume authoritative network data.

**When to skip:** A **[[Cloud]]** provider already owns the network inventory and IP address lifecycle. Also skip it for small estates where a spreadsheet or lighter IPAM is adequate, or for general application CMDB needs.

**Trade-offs:** The Apache 2.0 community edition has a strong data model and plugin ecosystem. Self-hosting adds PostgreSQL, upgrades, and plugin management. NetBox Cloud and Enterprise provide commercial deployment paths.

**Related garden:** Use **[[IaC]]** and **[[Ansible]]** as automation consumers. Use **[[LibreNMS]]** to observe live state. NetBox defines intended state rather than discovering or enforcing it by itself.

## Details

| Topic | Notes |
|-------|--------|
| **Role** | Defines intended network state; does not push configuration to devices itself |
| **Stack** | Python, Django, PostgreSQL, REST and **[[GraphQL]]** APIs, and a plugin architecture |
| **Core domains** | IPAM for prefixes, addresses, VLANs, and VRFs; DCIM for sites, racks, devices, cables, and circuits |
| **Editions** | Community open source, NetBox Cloud, and NetBox Enterprise |
| **Alternatives** | Nautobot for automation-heavy workflows; lighter IPAM tools; commercial DDI and CMDB suites |

**References**

- [NetBox documentation](https://docs.netbox.dev/en/stable/)
- [NetBox Community on GitHub](https://github.com/netbox-community/netbox)
- [NetBox Labs product page](https://netboxlabs.com/oss/netbox/)
