---
title: "nvm"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - nvm
  - nvm-sh

params:
  aliases:
    - nvm-sh
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - environment-managers
---

[nvm](https://github.com/nvm-sh/nvm) (Node Version Manager) installs and switches **[[Node.js]]** versions per shell session from `.nvmrc`. We **assess** it for Node-only estates; polyglot repos should prefer **[[mise]]** or **[[asdf]]**.

## Blurb

> nvm allows you to quickly install and use different versions of node via the command line.

## Summary

**What it is:** Bash/zsh script managing Node installs under `~/.nvm` with `nvm use` and `nvm install`.

**When to use:** JavaScript-heavy laptops with simple Node pinning needs.

**When to skip:** Need fast switching or Windows-first ergonomics (**[[fnm]]**). Multiple runtimes beyond Node.

**Key features:** `.nvmrc`, LTS aliases, npm global packages per Node version.


## Details

| Topic | Notes |
|-------|--------|
| **CI** | Prefer explicit Node version in **[[GitHub Actions]]** over relying on nvm in runners |
| **Contrast** | **[[fnm]]** for Rust-based speed; **[[mise]]** for all-in-one pins |

**References**

- [nvm README](https://github.com/nvm-sh/nvm#readme)
