---
title: "Git Worktree"
date: 2026-05-28
lastmod: 2026-05-28
draft: false

keywords:
  - Git Worktree

params:
  garden:
    kind: item
    usefulness: trial
    category: technique
    movement: "No Change"

aliases:
  - /radar/techniques/git-worktree
  - /radar/techniques/git-work-trees
  - /garden/git-work-trees/
---

[Git Worktree](https://git-scm.com/docs/git-worktree)

Git worktrees let one **[[git]]** repository hold several checked-out branches at once, each in its own directory. We **trial** the technique when parallel work beats stashing or re-cloning: feature branch plus PR review, hotfix while main stays clean, or agent tooling that needs an isolated checkout per branch.

## Blurb

> Manage multiple working trees attached to the same repository. A git repository can support multiple working trees, allowing you to check out more than one branch at a time.

## Summary

**What it is:** A repo has one **main worktree** (from `git clone` or `git init`) and zero or more **linked worktrees**. Each worktree shares the same object database but has its own `HEAD`, index, and files on disk. Git tracks metadata under `.git/worktrees/`.

**When to use:**

| Situation | Why worktrees help |
|-----------|-------------------|
| Feature + review | Keep `main` checked out while you review a **[[Pull Request]]** in another folder |
| Hotfix interrupt | Branch off production without disturbing in-progress edits |
| Parallel agents | Tools like **[[Cursor]]** best-of-N runners can use one worktree per attempt |
| Long builds | Run tests in one tree while you edit in another |

**When to skip:** Single-branch solo work with no context switching. Repos where disk space is tight (each tree duplicates the working copy). Teams that prefer one clone per branch in CI only.

**Core commands:**

| Command | Purpose |
|---------|---------|
| `git worktree add ../path branch` | New linked tree at `../path` on `branch` |
| `git worktree add -b new-branch ../path` | Create branch and check it out |
| `git worktree list` | Show all trees, paths, and checked-out refs |
| `git worktree remove ../path` | Drop a linked tree (branch stays) |
| `git worktree prune` | Clean stale admin files after manual deletes |

**Rules of thumb:** One branch per worktree at a time (Git blocks duplicate checkouts). Run `add` from the main repo; put sibling paths outside the main tree (`../feature-x`) to avoid nested folders. Remove linked trees when done so `.git/worktrees` stays tidy.

## Personal Experience

The reason this is a trial vs adopt is because it works different than normal `git` clone. IDEs can get confused, and they don't always play nice with [[Dev Container|devcontainers]], so your mileage may vary.

Our main usage is when we have to work on multiple branches at the same time (for example: `main`, `staging`, `prod`). In this case we structure things in a very specific way:

1. Create a directory to contain the worktrees
    1. `mkdir <repo name>`
    2. `cd <repo name>`
2. Clone the main worktree
    1. `git clone <repo url> main`
3. Create all other worktrees as siblings
    1. `cd main`
    2. `git worktree add ../staging staging`
    3. `git worktree add ../prod prod`
4. Use the correct directory / worktree for your work

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
