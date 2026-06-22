---
title: "CloudGraph"
date: 2026-05-28
lastmod: 2026-06-22
draft: false

keywords:
  - CloudGraph

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
aliases:
  - /radar/tools/cloudgraph
---

[CloudGraph](https://www.cloudgraph.dev/) is an open source GraphQL API and cloud security posture tool for AWS, Azure, GCP, and Kubernetes. It builds typed asset inventories, maps resource relationships, and ships built-in compliance checks (CIS, PCI, NIST). We **assess** it for multi-cloud visibility before picking a long-term CSPM stack.

## Blurb

> CloudGraph is the free open-source universal GraphQL API and Cloud Security Posture Management (CSPM) tool for AWS, Azure, GCP, and K8s.

## Summary

**What it is:** CLI and local GraphQL endpoint over scanned cloud accounts; query resources and edges across providers in one schema.

**When to use:** quick inventory across AWS plus GCP; compare stage vs prod in one query; ad hoc compliance posture reports; explore relationships (e.g. security groups to instances).

**When to skip:** need continuous agentless SaaS CNAPP with ticketing workflows; org standardized on **[[Kubescape]]** or a vendor CSPM; GraphQL ops overhead is unwanted.

**Key features:** CIS benchmark packs, historical snapshots, validated queries, enhanced AWS billing and CloudWatch fields (per upstream docs).


## Details

| Topic | Notes |
|-------|--------|
| **Install** | See [CloudGraph CLI](https://github.com/cloudgraphdev/cli) |
| **Scan** | Connect credentials per cloud; index into local GraphQL |
| **Query** | GraphQL over unified schema |

**Versus Kubescape:** Kubescape targets Kubernetes and supply-chain posture with admission and CI hooks; CloudGraph emphasizes cross-cloud GraphQL inventory and CSPM-style checks.

**References**

- [CloudGraph documentation](https://docs.cloudgraph.dev/)
- [GitHub repository](https://github.com/cloudgraphdev/cli)
