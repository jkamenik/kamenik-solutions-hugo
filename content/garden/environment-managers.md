---
title: "Environment Managers"
date: 2026-01-13
lastmod: 2026-05-18
draft: false

keywords:
  - Environment Managers
  - Environment Manager
  - Enviornment Managers

params:
  garden:
    kind: subcategory
    parent_category: tool
    subcategory_slug: environment-managers

aliases:
---

Under **[[Tool]]**, **Environment Managers** groups utilities that shape **what runs on your machine** when you develop: language/runtime versions, `PATH`, and per-project env vars. Goal is **reproducible local dev** without "works on my laptop" drift. Prefer **[[Dev Container]]** (**adopt**) for team-wide parity; use this bucket for **host-native** workflows and polyglot laptops.

**In this subcategory:**

| Tool / pattern | Rating | Use when |
|----------------|--------|----------|
| **[[Dev Container]]** | **adopt** (related) | Team standard dev image; env in OCI, not shell hooks |
| **[[direnv]]** | **assess** | Auto-load `.envrc` / `.env` per directory on `cd` |
| **mise** (asdf successor) | **assess** | One CLI for Node, Python, Terraform pins via `.mise.toml` |
| **asdf** | **assess** | Plugin ecosystem; legacy installs still common |
| **nvm / fnm** | **trial** | Node-only version switching |
| **pyenv / rbenv** | **assess** | Single-language version managers when mise is overkill |
| **Nix / flakes** | **assess** | Reproducible shells; heavier ops learning curve |
| **conda** | **assess** | Data science stacks with binary deps |

**What belongs here:**

- Version pins committed in repo (`.tool-versions`, `.nvmrc`, `.python-version`, `mise.toml`)
- Shell hooks that load project env (**[[direnv]]**)
- Local toolchain orchestration on the **host**

**What does not belong here:**

- **[[Dev Container]]** internals (document on that item; link when env is containerized)
- **[[GitHub Actions]]** / CI images (set env in workflow YAML, not direnv)
- Cloud **deployment** environments (**[[Kubernetes]]**, Terraform workspaces)
- Application **config** at runtime (**[[12 Factor App]]** env vars in prod)

**Garden stance:**

1. **Adopt** **[[Dev Container]]** (or equivalent) when more than one engineer ships the same service.
2. **Assess** **[[direnv]]** for multi-repo laptops and **[[cursor-agent]]** workflows that expect `.env` on `cd`.
3. **Assess** **mise** (or **asdf**) when repos pin different Node/Python/TF versions and you want one entrypoint.
4. Commit pin files; never commit secrets (`.env` gitignored, `.envrc` reviewed).

**How to tag:** **[[Tool]]** items with `subcategories: ["[[Environment Managers]]"]` when the product's main job is local dev environment or version management.
