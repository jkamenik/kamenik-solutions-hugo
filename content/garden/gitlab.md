---
title: GitLab
date: '2025-12-02'
lastmod: '2026-07-02'
draft: false
keywords:
- GitLab
params:
  garden:
    kind: item
    usefulness: trial
    category: platform
    movement: No Change
aliases:
- /radar/platforms/gitlab
---

[GitLab](https://gitlab.com/). Is an all-in-one DevSecOps **[[Platform]]** for **[[git]]** hosting, merge requests, built-in CI/CD, registry, and security scanning.

## Blurb

> Your intelligent orchestration platform for DevSecOps

## Summary

**Garden stance:** We **trial** GitLab for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

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
