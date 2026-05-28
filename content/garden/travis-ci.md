---
title: "Travis CI"
date: 2026-05-27
lastmod: 2026-05-27
draft: false

keywords:
  - Travis CI

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "No Change"
    subcategories:
      - ci-cd-tools

aliases:
  - /radar/tools/travis-ci
---

[Travis CI](https://www.travis-ci.com/) is a hosted continuous integration service tied closely to **[[GitHub]]** (historically the default for OSS `.travis.yml` builds). We **assess** it for legacy repos only. New pipelines should land on **[[GitHub Actions]]** unless a contract or org mandate says otherwise.

## Blurb

> Travis CI is a hosted continuous integration service used to build and test software projects hosted on GitHub and other providers.

## Summary

**Role:** **[[Continuous Integration]]** on push and pull request via `.travis.yml`; optional deploy stages for **[[Continuous Delivery]]** to cloud or static hosts.

**When to use:** an existing Travis pipeline still runs and migration cost exceeds near-term value; enterprise Travis.com matches compliance or billing requirements you cannot meet on Actions.

**When to skip:** new repositories; need OIDC to cloud deploys, reusable workflows, org-wide templates, or monorepo path filters (**[[GitHub Actions]]** and GitLab CI cover this better).

**Not the same as:** **[[GitHub Actions]]** (native GitHub workflows); **[[Jenkins]]** (self-hosted pet server, **hold**). Travis is hosted SaaS with YAML in-repo.

## Details

| Topic | Notes |
|-------|--------|
| **Config** | `.travis.yml` at repo root; language matrix, `script`, `before_install`, optional `deploy` |
| **History** | Travis CI Org (travis-ci.org) ended free public builds; Travis.com is the supported product |
| **Pricing** | Paid usage-based tiers only since 2021; no standing free tier for open source |
| **Secrets** | Encrypted variables in Travis settings; no first-class OIDC to AWS/GCP/Azure like Actions |
| **Runners** | Hosted Linux/macOS/Windows workers; concurrency limits depend on plan |
| **Integrations** | GitHub App or OAuth; Bitbucket and Perforce on enterprise **Server** tier |

**Migration off Travis:** use [GitHub Actions Importer](https://docs.github.com/en/actions/migrating-to-github-actions/automated-migrations/using-github-actions-importer-to-automate-migrations) for a dry-run, or hand-port matrix jobs to `.github/workflows/*.yml`. Remove `.travis.yml` and rotate any secrets that lived only in Travis.

**Practices for legacy repos:** pin base images; avoid long-lived cloud keys in Travis vars; set a migration deadline when credits or contract terms end.

**References**

- [Travis CI documentation](https://docs.travis-ci.com/)
- [Migrating from Travis CI to GitHub Actions](https://docs.github.com/en/actions/migrating-to-github-actions/manually-migrating-to-github-actions/migrating-from-travis-ci-to-github-actions)
