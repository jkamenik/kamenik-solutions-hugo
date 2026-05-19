---
title: "Git"
date: 2023-07-23
lastmod: 2026-05-18
draft: false

keywords:
  - Git

params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: "No Change"

aliases:
  - /radar/tools/git
---

[Git](https://git-scm.com/) is the default distributed version control system for every repo we touch: local branches, cheap merges, and a full history on each clone. We **adopt** it as the baseline under **[[Pull Request]]** / **[[GitOps]]** workflows on **[[GitHub]]** or **[[GitLab]]**; use **[[git lfs]]** when binaries or large assets would bloat history.

## Blurb

> Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

## Summary

**Core model:** commits point at snapshots of the tree; branches are movable refs; remotes sync packs of objects. Each developer has a full copy of history locally, so most work (branch, commit, diff) needs no network.

**Day-to-day loop:**

| Step | Command / concept |
|------|-------------------|
| Clone / fetch | `git clone`, `git fetch`, `git pull` |
| Branch | cheap local branches vs linear central VCS |
| Worktree | checked-out files you edit |
| Stage | index / staging area (`git add`, `git restore`) |
| Commit | immutable snapshot in the object store |
| Share | `git push` to **[[GitHub]]**, **[[GitLab]]**, or other remote |

**Why adopt over SVN / Perforce / ClearCase:**

- Branching and merging are normal, not exceptional
- Staging lets you craft commits before recording history
- Distributed workflow: review offline, push when ready
- Ecosystem: **[[GitHub Actions]]**, **[[GitOps]]**, **[[Policy as Code]]**, and every **[[Internal Developer Platform]]** assume Git

**Pair with:** `.gitattributes` (EOL normalization; complements **[[EditorConfig]]**), signed commits where policy requires, and **[[git lfs]]** for large blobs.

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

**Garden pattern:** **adopt** Git for all new code; default hosting is org **[[GitHub]]** unless a customer mandates **[[GitLab]]**.

**References**

- [Git](https://git-scm.com/)
- [Pro Git book](https://git-scm.com/book/en/v2)
