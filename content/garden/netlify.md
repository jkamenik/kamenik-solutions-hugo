---
title: Netlify
date: '2026-06-17'
lastmod: '2026-07-29'
draft: false
keywords:
- Netlify
params:
  garden:
    kind: item
    usefulness: assess
    category: platform
    movement: No Change
    subcategories:
    - ci-cd-tools
---

[Netlify](https://www.netlify.com/) is a platform we **assess** in the garden.

## Summary

**Key points:**

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
- [Netlify Build](https://www.netlify.com/platform/core/build/)## Personal Experience

<!-- User-owned: vault-only; never published or exported. Agents read for /tech-garden update synthesis; proofread spelling/grammar only. -->

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
