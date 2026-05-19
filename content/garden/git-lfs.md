---
title: "git lfs"
date: 2023-07-23
lastmod: 2026-05-18
draft: false

keywords:
  - git lfs

params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: "No Change"

aliases:
  - /radar/tools/git-lfs
---

[Git LFS](https://git-lfs.com/) is an open-source **[[git]]** extension that stores large blobs (binaries, media, datasets) outside the object database and keeps lightweight pointer files in history. We **adopt** it whenever checked-in assets would bloat clones or make `git log` unusable—typical on **[[GitHub]]** or **[[GitLab]]** repos with images, models, or build artifacts that must stay versioned.

## Blurb

> Git Large File Storage (LFS) replaces large files such as audio samples, videos, datasets, and graphics with text pointers inside Git, while storing the file contents on a remote server like GitHub.com or GitHub Enterprise.

## Summary

**Problem:** Git is optimized for text diffs; committing multi‑MB or GB files duplicates full blobs in every revision and slows clone/fetch for everyone.

**What LFS does:** On `commit`, matching paths are uploaded to LFS storage and replaced in the tree with small pointer files. On `checkout`, hooks swap pointers back to real files. Server-side, LFS stores file contents separately from the Git packfiles.

**When to use:** repos with PSDs, videos, ML weights, firmware images, or other binaries you need in VCS—not in object storage alone.

**When to skip:** generated artifacts that should never be committed; assets better served from a registry or CDN; repos where `git lfs` is not enabled on the host (fix hosting first).

**Pair with:** **[[git]]** as the base VCS; `.gitattributes` patterns via `git lfs track`; `git lfs migrate` to rewrite history when adding LFS to an existing repo.

## Details

**Setup (once per machine):**

```bash
git lfs install
```

**Per repository:**

1. Track patterns: `git lfs track "*.psd"` (writes/updates `.gitattributes`)
2. Commit `.gitattributes` with the patterns
3. Add and commit large files normally; `git push` uploads LFS objects to the remote LFS API

**Mental model:**

| Layer | Behavior |
|-------|----------|
| Working tree | Real file bytes you edit |
| Git commit | Pointer file in the tree for tracked extensions |
| LFS server | Content-addressed blob storage (GitHub/GitLab/self-hosted) |

**History migration:** Tracking in `.gitattributes` does not retroactively convert old commits. Use `git lfs migrate import` (or related subcommands) when adopting LFS on a repo that already committed large files.

**Hosting:** **[[GitHub]]** and **[[GitLab]]** ship LFS endpoints and quotas; self-hosted Git needs an LFS-compatible server. Same branch protections and access controls apply to LFS objects as to the rest of the repo.

**Operational notes:** clones need the LFS CLI installed or fetches omit real file content; CI runners must install `git-lfs` and run `git lfs pull` where needed; monitor LFS bandwidth/storage quotas on SaaS hosts.

**Security:** keep the client updated (e.g. [3.7.1+](https://github.com/git-lfs/git-lfs/security) for known advisories).

**Not the same as:** submodule-only binary repos without LFS; artifact registries (npm, OCI) for release binaries; **[[git]]** itself.

**References**

- [Git LFS](https://git-lfs.com/)
- [git-lfs/git-lfs documentation](https://github.com/git-lfs/git-lfs/tree/main/docs)
