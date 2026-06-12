---
title: "direnv"
date: 2024-10-01
lastmod: 2026-06-12
draft: false

keywords:
  - direnv

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "No Change"
    subcategories:
      - environment-managers
aliases:
  - /radar/tools/direnv
---

[direnv](https://direnv.net/) loads and unloads **per-directory environment variables** when you `cd` into a project (via a hook in bash/zsh/fish). We rate it **assess**: strong for host-shell and multi-repo local work; less critical when **[[Dev Container]]** or a VM already defines the toolchain.

## Blurb

> direnv is an extension for your shell. It augments existing shells with a new feature that can load and unload environment variables depending on the current directory.

## Summary

**What it does:** reads `.envrc` in the project root (bash-like DSL), exports vars for that directory tree, reverts when you leave. Common patterns:

- `dotenv` / `dotenv_if_exists` — load `.env` (keep `.env` gitignored, commit `.envrc`)
- `layout python`, `layout go` — wire language version managers
- `use nix`, `use flake` — enter Nix dev shells on `cd`

**When to assess / adopt locally:**

- Many repos on the laptop with different `PATH`, API keys, or tool versions
- **[[cursor-agent]]** / CLI agents that expect `.env` loaded automatically (see vault `agent-skills` README)
- Polyglot monorepos where each subdirectory needs its own env

**When to skip:**

- Primary dev is **[[Dev Container]]** or remote environments (env is in the image)
- Team policy forbids shell hooks on corporate laptops
- You only need one global profile (use shell profile or a single version manager instead)

**Security:** run `direnv allow` only after reviewing `.envrc`; treat untrusted clones like arbitrary shell scripts.

## Details

| Topic | Notes |
|-------|--------|
| **Install** | Package + `direnv hook zsh` (or bash) in `~/.zshrc` |
| **CI** | Do not rely on direnv in **[[GitHub Actions]]**; set env in workflow explicitly |
| **Secrets** | `.envrc` can reference `.env`; never commit secrets |
| **Pairing** | Fits **[[Environment Managers]]** bucket alongside version managers, not a replacement |

**References**

- [direnv documentation](https://direnv.net/docs/installation.html)
