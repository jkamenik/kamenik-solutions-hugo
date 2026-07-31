---
title: rg
date: '2026-07-31'
lastmod: '2026-07-31'
draft: false
keywords:
- rg
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: New
---

[rg](https://github.com/BurntSushi/ripgrep) is a fast, line-oriented code search tool that respects `.gitignore` by default. We **trial** it for replacing plain `grep` in day-to-day repository search.

## Blurb

> ripgrep is a line-oriented search tool that recursively searches the current directory for a regex pattern. By default, ripgrep will respect gitignore rules and automatically skip hidden files/directories and binary files.

## Summary

Use `rg` for fast recursive code search that honors ignore files, skips binaries and hidden files, and outputs colored matches with line numbers. Supports file-type filters (`-tpy`), context (`-C`), `--json`, and opt-in PCRE2 (`-P`) for lookaround. Current stable: **14.1.1**. Skip when a POSIX-ubiquitous tool is required; `grep` remains the portable standard.

## Details

- **Install:** `brew install ripgrep` (or static binaries per release).
- **License:** MIT / UNLICENSE (dual).
- **Language:** Rust; regex via the `regex` crate (DFA + SIMD).
- **Contrast:** supersedes `ag` (The Silver Searcher, unmaintained) and `ack`; outperforms GNU grep on Unicode and large repos. Vim/Emacs use `rg` as the `grep` backend by default.
