---
title: "Continuous Integration"
date: 2026-01-07
lastmod: 2026-06-12
draft: false

keywords:
  - Continuous Integration

params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "No Change"
aliases:
  - /radar/techniques/continuous-integration
---

[Continuous integration](https://en.wikipedia.org/wiki/Continuous_integration) (CI) means every change merged to the mainline is **built and verified automatically** before it becomes everyone else's baseline. We **adopt** CI for all products: small batches, fast feedback on **[[Pull Request]]**s, and a green `main` that feeds **[[Continuous Delivery]]** (and optionally **[[Continuous Deployment]]**).

## Blurb

> Continuous integration is the practice of merging all developers' working copies to a shared mainline several times a day.

## Summary

**What CI owns (stop here vs CD):**

| Stage | Technique | Outcome |
|-------|-----------|---------|
| PR + merge to main | **Continuous Integration** (**adopt**) | Compile/build, **[[Unit Testing]]**, lint, fast integration tests |
| Releasable artifact | **[[Continuous Delivery]]** (**adopt**) | Signed/published artifact; promote with gates |
| Auto to production | **[[Continuous Deployment]]** (**assess**) | No human promote |

**Typical CI pipeline on every PR and on `main` after merge:**

1. **Checkout** and dependency restore (cached)
2. **Build** (compile, bundle, image build if applicable)
3. **[[Code Linting]]** and static checks (**[[Shift Left]]**)
4. **Unit tests** and targeted integration tests (containers or test env as needed)
5. **Security/policy** scans on the PR path (**[[DevSecOps]]**, **[[Policy as Code]]** where IaC changes)
6. **[[Code Review]]** with required status checks before merge

**Practices we expect:**

- **Trunk-based flow:** short-lived branches; merge at least daily
- **Fix forward:** broken main is priority zero; revert if fix is not minutes away
- **Same commands locally and in CI** (`make test`, `npm test`, etc.)
- **Required checks** on protected `main`; no bypass without explicit process

**Tooling:** **[[GitHub Actions]]** (**adopt**) for repos on GitHub; avoid new **[[Jenkins]]** (**hold**) pet servers. See **[[CI-CD Tools]]** for the product bucket vs these technique notes.

**After CI succeeds:** hand off artifacts to delivery (registry, chart repo, installer) per **[[Continuous Delivery]]**. Deploy controllers (**[[ArgoCD]]**) run downstream of the build, not instead of it.

## Details

| Topic | Notes |
|-------|--------|
| **Scope** | CI proves the change integrates; it does not replace staging/system tests in CD |
| **Speed** | PR feedback under ~15 minutes for core paths; split slow suites |
| **Flakes** | Quarantine or fix; do not mute checks |
| **Monorepo** | Path filters so unrelated packages do not block the world |
| **Forks** | `pull_request` vs `pull_request_target` carefully; least privilege for untrusted code |

**References**

- [Wikipedia: Continuous integration](https://en.wikipedia.org/wiki/Continuous_integration)
