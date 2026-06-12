---
title: "GitHub Actions"
date: 2023-07-23
lastmod: 2026-05-18
draft: false

keywords:
  - GitHub Actions

params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: "No Change"
    subcategories:
      - ci-cd-tools
aliases:
  - /radar/tools/github-actions
---

[GitHub Actions](https://docs.github.com/en/actions) is GitHub's built-in CI/CD engine: event-driven workflows defined in `.github/workflows/*.yml`, executed on GitHub-hosted or self-hosted runners. We **adopt** it as the default **[[CI-CD Tools]]** plane for any repository on **[[GitHub]]**; pair cluster delivery with **[[ArgoCD]]** (build and push in Actions, sync in Argo) rather than imperative deploy scripts.

## Blurb

> Automate, customize, and execute your software development workflows right in your repository.

## Summary

**Role:** **[[Continuous Integration]]** on every push and pull request (build, test, lint, security scans); optional **[[Continuous Delivery]]** steps (artifacts, releases, environment promotions) without leaving the repo.

**When to use:** code lives on GitHub; you want branch protection, required checks, and workflow-as-code next to the application; you need marketplace actions, reusable workflows, or org-wide workflow templates.

**When to skip:** primary forge is **[[GitLab]]** (use GitLab CI instead); heavy Kubernetes-native pipeline CRDs are a deliberate platform choice (**[[Tekton]]**, **assess**); long-lived pet CI servers (**[[Jenkins]]**, **hold**) when Actions plus OIDC can replace them.

**Pairs with:** **[[Shift Left]]** and **[[DevSecOps]]** gates on the PR path; **[[Policy as Code]]** and third-party scanners (e.g. **[[Codacy]]**, **assess**) as required checks; **[[cursor-agent]]** for headless agent jobs in workflows when you are on Cursor billing.

**Not the same as:** **[[ArgoCD]]** (GitOps deploy controller for **[[Kubernetes]]**); **[[Argo Workflows]]** (in-cluster DAG workflows). Actions runs the pipeline; Argo CD reconciles desired cluster state after merge.

## Details

| Topic | Notes |
|-------|--------|
| **Workflows** | Triggers: `push`, `pull_request`, `schedule`, `workflow_dispatch`, labels, releases |
| **Reuse** | Callable workflows and composite actions; pin third-party actions to full SHAs |
| **Runners** | `ubuntu-latest` for most jobs; self-hosted only when hardware, network, or compliance requires it |
| **Secrets** | Repo/org secrets and environments; prefer **OIDC** (`id-token: write`) to cloud roles over static cloud keys in YAML |
| **Permissions** | Least-privilege `permissions:` at workflow or job level; avoid blanket `contents: write` |
| **Environments** | Protection rules and required reviewers for staging/production deploy jobs |
| **Artifacts & caches** | Pass build outputs between jobs; cache dependencies with stable keys |
| **Concurrency** | `concurrency` groups to cancel superseded PR runs and avoid deploy races |

**Practices we expect:** required status checks on `main`; no secrets in logs; dependabot or renovate for action and dependency bumps; separate workflows for PR validation vs release/deploy.

**References**

- [GitHub Actions documentation](https://docs.github.com/en/actions)
- [Security hardening](https://docs.github.com/en/actions/security-guides/security-hardening-for-github-actions)
- [OpenID Connect](https://docs.github.com/en/actions/deployment/security-hardening-your-deployments/about-security-hardening-with-openid-connect)
