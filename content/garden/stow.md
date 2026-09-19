---
title: Stow
date: '2026-09-18'
lastmod: '2026-09-18'
draft: false
keywords:
- Stow
params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: New
---

[GNU Stow](https://www.gnu.org/software/stow/) is a symlink farm manager that makes dotfiles appear installed in place. We **adopt** it as the dotfile mechanism in the tui-ide repo.

## Blurb

> GNU Stow is a symlink farm manager which takes distinct packages of software and/or data located in separate directories on the filesystem, and makes them appear to be installed in the same place.

## Summary

Use Stow with the Homebrew Bundle in the tui-ide repo. `install.sh` detects the OS, runs `brew bundle`, backs up conflicting files, then stows dotfiles on macOS and Linux.

It currently stows zsh, git, nvim, and herdr configs, with git identity kept in a git-ignored local file.

## Details

- **Upstream:** https://www.gnu.org/software/stow/
- **Role:** dotfile deployment in the TUI IDE stack
- **Companion:** Homebrew Bundle in the same repo
- **Stowed configs:** zsh, git, nvim, herdr
- **Related:** [[Dotfiles in Version Control]], [[git]], [[Zsh]]
