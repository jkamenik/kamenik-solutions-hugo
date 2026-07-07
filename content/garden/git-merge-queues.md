---
title: Git Merge Queues
date: '2026-06-26'
lastmod: '2026-07-02'
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
    movement: No Change
---

[Git Merge Queues](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-a-merge-queue). A [merge queue](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-a-merge-queue) serializes merges into a busy default branch.

## Blurb

> You can increase development velocity with a merge queue for pull requests in your repository.

## Summary

**Garden stance:** We **trial** Git Merge Queues for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

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
