---
title: "GitHub"
date: 2024-10-01
lastmod: 2026-06-12
draft: false

keywords:
  - GitHub

params:
  garden:
    kind: item
    usefulness: adopt
    category: platform
    movement: "No Change"
aliases:
  - /radar/platforms/github
---

[GitHub](https://github.com/) is the default **[[Platform]]** for hosting **[[git]]** repos, collaboration, and the surrounding delivery toolchain. We **adopt** it as org-standard forge unless a customer or compliance boundary requires **[[GitLab]]**—then mirror the same practices (**[[Pull Request]]**, protected `main`, **[[GitHub Actions]]** or equivalent CI, **[[GitOps]]** from the default branch).

## Blurb

> The complete developer platform to build, scale, and deliver secure software.

## Summary

**What it is:** SaaS (or **GitHub Enterprise**) for Git remotes, issues, discussions, releases, and integrations—plus first-party products (Actions, Packages, Codespaces, Advanced Security) on top of the same repo graph.

**Why adopt:** largest ecosystem (marketplace actions, OIDC to cloud, Dependabot, branch protection APIs); default for OSS and most vendors; **[[GitHub Actions]]** and **[[Policy as Code]]** / scanner apps assume GitHub as the control plane.

**When to use:** new org or product repos; public or private code; PR-based **[[Code Review]]**; CI/CD via **[[GitHub Actions]]**; **[[git lfs]]** for large assets; GitHub Pages or release assets when appropriate.

**When to use GitLab instead:** customer mandate, air-gapped self-managed GitLab, or all-in-one DevOps on GitLab CI without Actions.

**Not the same as:** **[[git]]** (the VCS protocol and CLI); **[[GitHub Actions]]** (CI/CD only); **[[GitOps]]** (deploy pattern); **[[GitLab]]** (competing platform).

## Details

| Capability | Garden link / note |
|------------|-------------------|
| Version control | **[[git]]** remotes; forks; default branch policies |
| Review & merge | **[[Pull Request]]**, required reviewers, CODEOWNERS |
| CI/CD | **[[GitHub Actions]]** (`.github/workflows/`) |
| Large files | **[[git lfs]]** (hosting quotas apply) |
| Delivery pattern | **[[GitOps]]**—repo as truth; Actions build, cluster tools sync |
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
