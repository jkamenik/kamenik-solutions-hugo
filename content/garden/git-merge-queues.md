---
title: Git Merge Queues
date: '2026-06-26'
lastmod: '2026-06-30'
draft: false
keywords:
- Git Merge Queues
- Merge Queue
- GitHub Merge Queue
params:
  aliases:
  - Merge Queue
  - GitHub Merge Queue
  garden:
    kind: item
    usefulness: trial
    category: technique
    movement: New
---

[Git Merge Queues](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-a-merge-queue)

A [merge queue](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-a-merge-queue) serializes merges into a busy default branch. It tests each **[[Pull Request]]** against the latest base plus queued changes before landing. We **trial** merge queues on high-velocity repos where "require branch up to date" slows teams without catching integration failures. **[[GitHub]]** ships merge queue natively; **[[GitLab]]** offers merge trains with similar goals.

## Blurb

> A merge queue helps increase velocity by automating pull request merges into a busy branch and ensuring the branch is never broken by incompatible changes.

## Summary

**What it is:** a FIFO queue on the Git host that batches pending PRs, builds a temporary integration branch, runs required **[[Continuous Integration]]** checks, and merges only when the combined result is green. It replaces the manual rebase-and-wait loop that branch protection often forces.

**Problem it solves:** two PRs can pass CI in isolation yet break `main` when both land. Merge queues test the exact post-merge graph before any commit reaches the default branch.

**When to use:**

| Signal | Fit |
|--------|-----|
| Many contributors merge to one branch daily | Strong |
| Required status checks on protected `main` | Required baseline |
| Flaky or slow CI | Tune concurrency first; queue adds wait time |
| Low merge volume or solo maintainer | Usually skip |

**When to skip:** repos with rare merges, no branch protection, or CI that cannot run on synthetic merge branches.

**Host support:**

| Host | Feature | CI hook |
|------|---------|---------|
| **[[GitHub]]** | Merge queue | `merge_group` event in **[[GitHub Actions]]** (or push to `gh-readonly-queue/<base>`) |
| **[[GitLab]]** | Merge trains | Pipeline rules for merge-train refs |

**Pairs with:** required status checks, **[[Pull Request]]** review, small diffs, and fast reliable tests. Not a substitute for **[[Code Review]]** or pre-merge lint gates on the PR itself.

## Details

**Enable on GitHub:**

1. Branch protection on the target branch: **Require merge queue**.
2. Keep **Require status checks to pass before merging** with the same checks you trust on PRs.
3. Update CI workflows to listen for `merge_group` (GitHub Actions) or pushes to `gh-readonly-queue/<base_branch>`.

**GitHub Actions trigger (minimal):**

```yaml
on:
  pull_request:
    branches: [main]
  merge_group:
    branches: [main]
```

**Operator flow:** author opens a PR, checks pass, clicks **Merge when ready**. The host enqueues the change, runs integration CI, merges on green, or removes the PR and notifies the author on failure.

**Queue settings worth tuning:**

| Setting | Tradeoff |
|---------|----------|
| Merge method (squash vs merge commit) | Team policy; document once |
| Build concurrency | Higher throughput vs runner cost |
| Jump to top of queue | Rebuilds in-flight work; use sparingly |

**Failure modes:** CI not wired to `merge_group` leaves the queue stuck waiting for checks. Third-party CI must explicitly trigger on the readonly queue branch pattern. A failed queued PR is dropped; the author fixes and re-enqueues.

**Alternatives:** strict "branch must be up to date" without a queue (more author toil). Third-party bots (e.g. Mergify) where the host has no native queue. **[[GitLab]]** merge trains for GitLab-only estates.
