---
title: "fnm"
date: 2026-06-12
lastmod: 2026-06-12
draft: false

keywords:
  - fnm

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
    subcategories:
      - environment-managers
---

[fnm](https://github.com/Schniz/fnm) (Fast Node Manager) is a Rust-based **[[Node.js]]** version manager with `.node-version` / `.nvmrc` support and cross-platform shells. We **trial** it over **[[nvm]]** when developers want faster Node switching on macOS and Linux.

## Blurb

> fnm is a fast and simple Node.js version manager, built in Rust.

## Summary

**What it is:** Single binary, `fnm use`, auto-switch on directory change (optional), Corepack-friendly.

**When to use:** Node-only version management with better performance than nvm.

**When to skip:** Already standardized on **[[mise]]** / **[[asdf]]** for all runtimes.

**Key features:** Multi-platform, `.node-version`, fish/zsh/bash support, `--use-on-cd` hook.

## Details

| Topic | Notes |
|-------|--------|
| **Migration** | Reads `.nvmrc` for compatibility with nvm-based repos |
| **Contrast** | **[[nvm]]** where shell-only legacy scripts dominate |

**References**

- [fnm documentation](https://github.com/Schniz/fnm#readme)
