---
title: "GitLab"
date: 2025-12-02
lastmod: 2026-06-12
draft: false

keywords:
  - GitLab

params:
  garden:
    kind: item
    usefulness: trial
    category: platform
    movement: "No Change"
aliases:
  - /radar/platforms/gitlab
---

[GitLab](https://gitlab.com/) is an all-in-one DevSecOps **[[Platform]]** for **[[git]]** hosting, merge requests, built-in CI/CD, registry, and security scanning. We rate it **trial** at org level because **[[GitHub]]** is the default.  Use GitLab when a customer, regulator, or air-gapped deployment requires it, then apply the same discipline (**[[Pull Request]]** / MR review, protected default branch, pipeline gates, **[[GitOps]]** from `main`).

## Blurb

> Your intelligent orchestration platform for DevSecOps: from planning to source code management to CI/CD, everything you need to build and ship software faster in one platform.

## Summary

**What it is:** SaaS **GitLab.com** or self-managed **GitLab** / Dedicated with a single application for repos, issues, wiki, CI (`.gitlab-ci.yml`), container/package registry, and integrated SAST/SCA/secret/DAST in merge requests.

**Why trial (not default):** **[[GitHub]]** has the broader marketplace, our existing **[[GitHub Actions]]** investment, and typical vendor integrations; GitLab wins on consolidated DevSecOps UI, self-hosted/air-gap, and customer mandates.

**When to use:** customer hosts on GitLab; compliance needs self-managed or isolated instance; team standardizes on GitLab CI and built-in security scanners instead of Actions plus third-party apps.

**When to stay on GitHub:** greenfield org repos, OSS publishing, and stacks that assume GitHub OIDC, Actions, or Dependabot.

**Not the same as:** **[[git]]** (VCS); **[[GitHub]]** (default platform); **[[GitHub Actions]]** (GitHub-only CI); **[[GitOps]]** (delivery pattern).

## Details

| Capability | Notes |
|------------|--------|
| Version control | **[[git]]** remotes; forks; protected branches |
| Review | Merge requests (same role as **[[Pull Request]]** on GitHub) |
| CI/CD | GitLab CI pipelines in `.gitlab-ci.yml`; includes, rules, environments |
| Registry | Container and package registry in-platform |
| Security | SAST, dependency scanning, secrets, DAST in MR; **[[DevSecOps]]** / **[[Shift Left]]** alignment |
| Large files | **[[git lfs]]** supported; quota per tier |
| Self-hosted | Common for public sector, telecom, and air-gap |

**Practices when GitLab is required:**

- Mirror GitHub norms: no direct pushes to `main`; required pipeline success; CODEOWNERS / approval rules
- Prefer CI/CD variables and OIDC/job tokens over long-lived deploy keys where available
- Use merge request templates and security scan results in the MR, not email-only review
- Keep **[[git]]** workflows portable, branch naming, conventional commits, and **[[GitOps]]** repos work the same; only the forge and CI YAML differ

**GitLab vs GitHub (quick map):**

| GitHub | GitLab |
|--------|--------|
| Pull request | Merge request |
| **[[GitHub Actions]]** | GitLab CI |
| GitHub Packages | GitLab registry |
| Dependabot | Dependency scanning / Renovate-style bots |

**References**

- [GitLab](https://gitlab.com/)
- [GitLab Docs](https://docs.gitlab.com/)
- [About GitLab](https://about.gitlab.com/)
