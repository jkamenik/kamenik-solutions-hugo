---
title: GitHub
date: '2024-10-01'
lastmod: '2026-07-02'
draft: false
keywords:
- GitHub
params:
  garden:
    kind: item
    usefulness: adopt
    category: platform
    movement: No Change
aliases:
- /radar/platforms/github
---

[GitHub](https://github.com/). Is the default **[[Platform]]** for hosting **[[git]]** repos, collaboration, and the surrounding delivery toolchain.

## Blurb

> Join the world's most widely adopted, AI-powered developer platform where millions of developers, businesses, and the largest open source community build software that advances humanity.

## Summary

**Garden stance:** We **adopt** GitHub for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

| Capability | Garden link / note |
|------------|-------------------|
| Version control | **[[git]]** remotes; forks; default branch policies |
| Review & merge | **[[Pull Request]]**, required reviewers, CODEOWNERS |
| CI/CD | **[[GitHub Actions]]** (`.github/workflows/`) |
| Large files | **[[git lfs]]** (hosting quotas apply) |
| Delivery pattern | **[[GitOps]]**, repo as truth; Actions build, cluster tools sync |
| Security | Dependabot, secret scanning, branch protection; pair with **[[Shift Left]]** / **[[DevSecOps]]** checks |

**Org practices we expect:**

- Repos under the org (not personal accounts) for team work
- Protected `main` / `release/*`; no direct pushes; required status checks
- Least-privilege GitHub Apps or fine-grained PATs; prefer OIDC from Actions to cloud over long-lived keys
- `.github` org templates for workflows, issue forms, and security policy where it helps consistency
- Document exceptions when a repo must live elsewhere (customer fork, mirror, legacy host)

**Enterprise / compliance:** GitHub Enterprise Cloud or Server when SSO, audit log retention, or data residency requires it; align with customer identity (SAML/OIDC) and IP allow lists as needed.

**References**

- [GitHub](https://github.com/)
- [GitHub Docs](https://docs.github.com/)
- [About GitHub](https://github.com/about)
