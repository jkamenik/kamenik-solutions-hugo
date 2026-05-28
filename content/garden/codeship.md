---
title: "CodeShip"
date: 2026-05-27
lastmod: 2026-05-27
draft: false

keywords:
  - CodeShip

params:
  garden:
    kind: item
    usefulness: hold
    category: platform
    movement: "New"
    subcategories:
      - ci-cd-tools

aliases:
  - /radar/platforms/codeship
---

[CodeShip](https://www.cloudbees.com/products/codeship) is a hosted CI service (CloudBees) for building and testing from Git repos. We **hold** it for net-new work: the product line is legacy relative to **[[GitHub Actions]]** and CloudBees' Jenkins-focused road map. Keep only where a pipeline still runs on CodeShip and migration is scheduled.

## Blurb

> CodeShip helps teams release software faster by automating build and test workflows in the cloud.

## Summary

**When to use:** sustaining existing CodeShip projects until decommission; short-term bridge during a CI migration plan.

**When to skip:** any new repository or service; standardize on **[[GitHub Actions]]**, **[[GitLab]]**, or self-hosted **[[Jenkins]]** only when required by policy.

**Migration hint:** reproduce `codeship.yml` steps as Actions workflows or reusable workflows; rotate secrets into GitHub OIDC or org vaults during cutover.
