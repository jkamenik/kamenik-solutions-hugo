---
title: Dokploy
date: '2026-07-20'
lastmod: '2026-07-20'
draft: false
keywords:
- Dokploy
params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: No Change
    subcategories:
    - ci-cd-tools
---

[Dokploy](https://dokploy.com/) markets itself as a self-hosted PaaS. In practice it is mostly a UI for **[[second touch provisioning]]** on hosts you already own. We **hold** it for greenfield unless hosts are treated as **[[Cattle Not Pets]]**.

## Blurb

> Simplify Application and Database Deployments

## Summary

**Why hold:** Marketing says PaaS. The real job is second-touch work: ship apps, Compose stacks, TLS, and DBs onto machines that **[[First Touch Provisioning]]** already created. That is useful UI, not a platform that abstracts the host fleet. Without cattle-style host automation, Dokploy encourages pet servers you babysit through a dashboard.

**When it might still fit:** Lab or single-node experiments. Or an estate where first touch replaces hosts as cattle and Dokploy only handles app deploy on top. Even then, prefer patterns that keep **[[Cattle Not Pets]]** (image rebuild, replace, not SSH snowflakes).

**When to skip:** New platforms. Prefer **[[Kubernetes]]** or managed PaaS (**[[Netlify]]** and peers) when you want real platform abstraction. The garden already **holds** **[[Docker Swarm]]**; Dokploy is Swarm-native under the hood.

**Key trade-offs:**

| Topic | Notes |
|-------|--------|
| **True role** | Second-touch control plane (deploy, Traefik, DB backups, roles) on your VMs |
| **Not** | A PaaS that owns first-touch cattle lifecycle for you |
| **Runtime** | Docker Swarm based; Compose without K8s |
| **Build** | Dockerfile, Nixpacks, Heroku Buildpacks, Compose |
| **Risk** | Dashboard-driven pets; Swarm path vs **[[Kubernetes]]** **adopt** |

**References**

- [Dokploy](https://dokploy.com/)
- [Dokploy GitHub](https://github.com/Dokploy/dokploy)
- [Self-hosted PaaS overview](https://dokploy.com/self-hosted-paas)

## Details

| Topic | Notes |
|-------|--------|
| **Install** | Single-script install on a VPS; Cloud option for hosting the control plane |
| **Deploy targets** | Same server or remote servers; Swarm for multi-node |
| **Templates** | One-click open source apps (e.g. Supabase, Cal.com, PocketBase) |
| **Monitoring** | Real-time CPU, memory, network; notifications on deploy success/fail |
| **Positioning** | Markets as open source alternative to Vercel, Netlify, and Heroku |
| **Peers (not in garden)** | Coolify, Dokku, CapRover share the same second-touch shape |
