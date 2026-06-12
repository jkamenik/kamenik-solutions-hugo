---
title: "Pull Request"
date: 2026-05-05
lastmod: 2026-06-12
draft: false

keywords:
  - Pull Request
  - Merge Request
  - PR

params:
  aliases:
    - Merge Request
    - PR
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "No Change"
---

[Pull Request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)

A [pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) (PR) proposes merging a branch into a shared mainline. **[[GitHub]]** calls it a pull request; **[[GitLab]]** calls it a merge request (MR). We **adopt** PRs as the front door to **[[Continuous Integration]]**: humans do **[[Code Review]]** while machines report lint, test, and scan status on the same change.

Even solo developers should open a PR against `main`. Automated gates catch issues that local habit misses.

## Blurb

> Pull requests let you propose, review, and merge code changes.

## Summary

**What a PR is:** a durable thread for a proposed diff (description, commits, file changes, checks, comments) before merge. It is not a Git primitive; hosts (**[[GitHub]]**, **[[GitLab]]**, Gerrit, Bitbucket) implement the workflow on top of **[[git]]** branches.

**What belongs on the PR:**

| Layer | Examples | Garden links |
|-------|----------|--------------|
| Human | Design, risk, operability, product fit | **[[Code Review]]** |
| Machine | Lint, unit tests, SAST, IaC policy | **[[Code Linting]]**, **[[Conftest]]**, **[[Semgrep]]**, **[[GitHub Actions]]** |

**When to use:** every change to shared repos (app code, **[[GitOps]]** config, **[[Policy as Code]]** bundles). Draft PRs are fine for work-in-progress without requesting review.

**When to skip:** none for team repos. For throwaway local branches, still mirror the same checks before push if you truly merge without a host PR (discouraged).

**Pairs with:** protected default branch; required status checks; **[[Shift Left]]** (find defects before production); **[[DevSecOps]]** (security findings are PR backlog, not a separate audit).

**Not the same as:** **[[Code Review]]** (the human practice); **[[Continuous Integration]]** (the verify-on-merge discipline). The PR is where both meet.

## Details

| Topic | Notes |
|-------|--------|
| **Size** | Small, reviewable diffs; one logical change per PR when possible |
| **Description** | What changed, why, how to test, links to tickets |
| **Checks tab** | Required green CI before merge; see **[[Continuous Integration]]** |
| **CODEOWNERS** | Route sensitive paths to qualified reviewers |
| **Merge strategies** | Squash vs merge commit is a team policy choice; document it |
| **IaC / GitOps** | Same PR pattern for Terraform, K8s, and policy repos |

**Vendor terms:**

| Host | Name |
|------|------|
| **[[GitHub]]** | Pull request (PR) |
| **[[GitLab]]** | Merge request (MR) |
| Gerrit | Change |

**References**

- [GitHub: About pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)
- [Atlassian: Making a pull request](https://www.atlassian.com/git/tutorials/making-a-pull-request)
