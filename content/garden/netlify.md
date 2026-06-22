---
title: "Netlify"
date: 2026-06-17
lastmod: 2026-06-22
draft: false

keywords:
  - Netlify

params:
  garden:
    kind: item
    usefulness: assess
    category: platform
    movement: "New"
    subcategories:
      - ci-cd-tools
---

[Netlify](https://www.netlify.com/) is a managed web platform for Jamstack sites, branch previews, and serverless backends. We **assess** it for client frontends and preview-heavy workflows. Our default static host remains **[[GitHub]]** Pages unless a project needs Netlify primitives or a customer already runs there.

## Blurb

> Create with AI or code, deploy instantly on production infrastructure. One platform to build and ship.

## Summary

**What it is:** Git-connected build and deploy, global CDN, HTTPS, deploy previews per branch or **[[Pull Request]]**, plus platform primitives (serverless functions, edge functions, forms, blobs, and managed Postgres).

**When to use:** marketing sites or SPAs that want one vendor for CI, hosting, and light backend APIs; teams that rely on shareable preview URLs for every change; frameworks with first-class Netlify adapters (Next.js, Astro, Hugo, and others).

**When to skip:** workloads that belong on **[[Kubernetes]]** or a hyperscaler; org standard is **[[GitHub Actions]]** plus **[[GitHub]]** Pages; need deep VPC peering, private backends, or heavy data-plane control.

**Not the same as:** **[[GitHub]]** (forge plus Pages); **[[GitHub Actions]]** (CI only); **[[Harness.io]]** (enterprise CD suite). Netlify is frontend-centric hosting with integrated build pipelines.


## Details

| Topic | Notes |
|-------|--------|
| **Deploy paths** | Git push, Netlify CLI, drag-and-drop, or dashboard prompts |
| **Config** | `netlify.toml` for build command, publish dir, redirects, headers, and plugins |
| **Previews** | Unique URL per branch and PR; one-click production deploy or rollback |
| **Primitives** | Functions, Edge Functions, Background and Scheduled Functions, Blobs, Netlify Database |
| **Edge** | Global CDN with HTTPS and DDoS protection on by default; High-Performance Edge on Enterprise |
| **Pricing** | Credit-based tiers; Free includes limited monthly credits; Pro and Enterprise add seats, SLAs, and support |

**Typical workflow:** connect a **[[GitHub]]** (or GitLab/Bitbucket) repo, set build command and output directory, enable deploy previews on PRs, add env vars per context (production vs preview), and use redirects for SPA routing or legacy paths.

**Pairs with:** static site generators (Hugo, Astro, Next.js static export), headless CMS webhooks for rebuild-on-publish, and light API routes via functions when a full **[[Kubernetes]]** service is overkill.

**References**

- [Netlify](https://www.netlify.com/)
- [Netlify Docs](https://docs.netlify.com/)
- [Platform primitives](https://docs.netlify.com/start/core-concepts/primitives/)
- [Netlify Build](https://www.netlify.com/platform/core/build/)
