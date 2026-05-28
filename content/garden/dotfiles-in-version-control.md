---
title: "Dotfiles in Version Control"
date: 2026-05-27
lastmod: 2026-05-27
draft: false

keywords:
  - Dotfiles in Version Control

params:
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: "New"

aliases:
  - /radar/techniques/dotfiles-in-version-control
---

Version-controlled dotfiles are shell, editor, and tool configs kept in a **[[git]]** repo so a machine can be rebuilt from a known baseline. We **assess** the practice: high value for solo reproducibility, but team standardization and secret hygiene need clear rules before **adopt**.

## Blurb

> Dotfiles are plain-text configuration files for Unix tools, typically stored in a home directory and named with a leading dot.

## Summary

**What it covers:** `.zshrc`, `.vimrc`, Starship, tmux, Homebrew Brewfile, and similar personal setup committed beside a README and install script (or [[Declarative IaC]]-style bootstrap).

**When to use:** you rebuild laptops often, want the same shell aliases everywhere, or document "how your machine is configured" for yourself.

**When to skip:** orgs that mandate MDM-only laptops with no local customization; shared secrets in dotfiles (use a secrets manager instead); duplicating what Nix/Home Manager or a golden AMI already provides.

**Pairs with:** private repo or public repo with a secrets scrub checklist; symlink or copy install script; optional chezmoi/yadm if dotfiles span multiple machines.
