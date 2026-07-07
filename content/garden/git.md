---
title: git
date: '2023-07-23'
lastmod: '2026-07-02'
draft: false
keywords:
- git
params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: No Change
aliases:
- /radar/tools/git
---

[git](https://git-scm.com/). Is the default distributed version control system for every repo we touch: local branches, cheap merges, and a full history on each clone.

## Summary

**Garden stance:** We **adopt** git for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

**Under the hood (practical mental model):** Git stores content-addressed objects (blobs, trees, commits) in an append-only object database. The index tracks what the next commit will contain; the working tree is your checkout on disk. You do not need to master plumbing to use Git well, but knowing "commit = snapshot + parent pointer" explains rebases and merge results.

**Merge philosophy:** Git reconciles toward a consistent working tree, not strict chronological file history. It replays or combines commits so the checkout matches intent; when two sides change the same lines irreconcilably, you get a **merge conflict** with conflict markers. You edit the merged file, `git add`, commit, and push so teammates inherit the resolution. Centralized tools that enforce linear locks on paths tend to conflict more often because they privilege checkout order over current tree state.

**Common commands (reference):**

| Area | Examples |
|------|----------|
| History | `git log`, `git show`, `git blame` |
| Undo | `git revert`, `git reset` (know soft/mixed/hard) |
| Sync | `git pull --rebase`, `git merge`, `git rebase` |
| Hygiene | `git stash`, `git clean`, `git gc` |

**Team practices:** trunk-based or short-lived branches; **[[Pull Request]]** as the review gate; protected `main`; no force-push to shared branches without agreement. For infrastructure and config, treat the repo as source of truth (**[[GitOps]]**).

**Not the same as:** **[[GitHub]]** / **[[GitLab]]** (hosting + collaboration); **[[GitOps]]** (delivery pattern); **[[git lfs]]** (large file extension).

**References**

- [Git](https://git-scm.com/)
- [Pro Git book](https://git-scm.com/book/en/v2)
