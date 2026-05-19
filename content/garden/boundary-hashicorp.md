---
title: "Boundary (Hashicorp)"
date: 2023-07-23
lastmod: 2026-05-18
draft: false

keywords:
  - Boundary (Hashicorp)

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "No Change"

aliases:
  - /radar/tools/boundary-hashicorp
---

[HashiCorp Boundary](https://developer.hashicorp.com/boundary) is an identity-aware proxy for **just-in-time** access to hosts and services (SSH, RDP, databases, Kubernetes) without handing users long-lived credentials or flat network VPNs. We rate it **assess**: strong fit for **[[ZTNA]]** / **[[Access on Demand]]** patterns when you already run the HashiCorp stack; prove ops appetite before committing (controllers, workers, Vault integration, session recording).

## Blurb

> Boundary provides identity-based access to dynamic infrastructure with fine-grained authorizations and session visibility.

## Summary

**What it does:** brokers connections after **OIDC**/SSO auth; issues short-lived credentials (often via Vault); logs sessions for audit. Replaces “SSH keys on a bastion” and broad **[[Tailscale]]**-style network access when you only need specific targets.

**When to assess:** multi-cloud or dynamic infra (Nomad, VMs, K8s) with compliance pressure for no standing privilege; teams standardizing on HashiCorp (**[[Terraform]]**, Vault) and wanting one access plane.

**When to skip:** simple static fleets with mature SSO + AoD elsewhere; orgs avoiding HashiCorp post-IBM acquisition complexity; need full L3 VPN (use Tailscale sparingly, not Boundary).

**Editions:** Community (self-managed), Enterprise, and HCP Boundary (managed). Match edition to audit requirements (session recording, multi-tenancy).

## Details

| Topic | Notes |
|-------|--------|
| **Identity** | Entra, Okta, Ping, or any OIDC IdP, pairs with **[[Auth0]]**-class providers at the edge |
| **Secrets** | Dynamic credentials via Vault; plan Vault HA before Boundary production |
| **Model** | Targets, host catalogs, roles; map to **[[RBAC]]** and break-glass runbooks |
| **Technique** | Implements **[[Zero Trust Network Architecture]]** principles in practice |
