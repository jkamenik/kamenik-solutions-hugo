---
title: Vim
date: '2026-07-23'
lastmod: '2026-07-23'
draft: false
keywords:
- Vim
- VI
- VI / VIM
- Vi
params:
  aliases:
  - VI
  - VI / VIM
  - Vi
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: Moved In
    subcategories:
    - ide
---

[Vim](https://www.vim.org/) is the ubiquitous modal text editor shipped as `vi` on many UNIX systems. We **adopt** its stock configuration and basic bindings as a portable operational baseline.

## Blurb

> Vim is a highly configurable text editor built to make creating and changing any kind of text very efficient.

## Summary

Use the basic vi/Vim command set for reliable editing on servers, containers, recovery shells, and unfamiliar machines. Keep the configuration unmodified so the same muscle memory works wherever `vi` is available.

Do not recreate a full IDE through Vim plugins when [[Cursor]] or [[Emacs]] already covers personal development. The value here is universal availability and baseline proficiency, not a customized daily-driver environment.

## Details

- **Upstream:** https://www.vim.org/
- **Core model:** Modal editing through normal, insert, visual, and command-line modes
- **Estate pattern:** Leave `vi` unmodified and rely on bindings available nearly everywhere
- **Required competence:** Navigate, insert, delete, search, save, and exit without local configuration
- **Availability:** Commonly present as `vi` or `vim` on UNIX and macOS toolchains
- **Primary editors:** [[Emacs]] or [[Cursor]] for personal development
- **Fit:** [[Tool]] / [[IDE]] when primary; otherwise a ubiquitous CLI utility
