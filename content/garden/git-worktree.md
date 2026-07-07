---
title: Git Worktree
date: '2026-05-28'
lastmod: '2026-07-02'
draft: false
keywords:
- Git Worktree
params:
  garden:
    kind: item
    usefulness: trial
    category: technique
    movement: No Change
aliases:
- /radar/techniques/git-worktree
---

[Git Worktree](https://git-scm.com/docs/git-worktree)

Git worktrees let one **[[git]]** repository hold several checked-out branches at once, each in its own directory. We **trial** it under **[[Technique]]** in the garden.

## Summary

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

**Versus alternatives:**

| Approach | Trade-off |
|----------|-----------|
| `git stash` | Fast, but only one checkout; easy to lose context in a deep stash stack |
| Second `git clone` | Fully isolated, but doubles fetch/storage and drift between clones |
| Worktree | Shared objects, one remote config; must respect one-branch-per-tree rule |

**Detached HEAD trees:** `git worktree add --detach ../experiment` gives a throwaway checkout for spikes or reproducing a bug at a specific commit without creating a branch.

**Lock and move:** `git worktree lock` prevents accidental removal (useful on shared machines). `git worktree move` relocates a tree if you reorganize directories.

**Cleanup:** If you delete a worktree folder by hand, run `git worktree prune`. Use `git worktree repair` after path moves or corrupted admin metadata.

**Garden stance:** **Trial** on any repo where you already **adopt** **[[git]]** and regularly switch branches mid-task. Promote to **adopt** once worktrees are part of your default local workflow.

**References**

- [git-worktree](https://git-scm.com/docs/git-worktree)
- [Pro Git: Git Tools - Worktrees](https://git-scm.com/book/en/v2/Git-Tools-Advanced-Merging#_worktrees)
