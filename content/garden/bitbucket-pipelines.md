---
title: "Bitbucket Pipelines"
date: 2026-05-27
lastmod: 2026-05-27
draft: false

keywords:
  - Bitbucket Pipelines

params:
  garden:
    kind: item
    usefulness: assess
    category: platform
    movement: "New"
    subcategories:
      - ci-cd-tools

aliases:
  - /radar/platforms/bitbucket-pipelines
---

[Bitbucket Pipelines](https://bitbucket.org/product/features/pipelines) is Atlassian's hosted CI service for Bitbucket Cloud repos. YAML-defined steps run in Docker images on Atlassian infrastructure. We **assess** it when the org is already on Bitbucket; default path for new work remains **[[GitHub Actions]]** unless licensing or data residency forces Bitbucket.

## Blurb

> Bitbucket Pipelines brings continuous integration and delivery to Bitbucket Cloud, powered by Docker.

## Summary

**Model:** `bitbucket-pipelines.yml` in the repo defines pipelines, branches, and deployment steps. Runners are managed; you bring container images and secrets via Bitbucket variables.

**When to use:** product code lives in Bitbucket Cloud; Jira/Confluence integration matters; you need Atlassian's compliance story without self-hosting Jenkins.

**When to skip:** greenfield repos on **[[GitHub]]** / **[[GitLab]]**; heavy custom runner fleets (compare self-hosted Actions or GitLab runners); teams standardized on **[[GitOps]]** tooling that assumes GitHub.
