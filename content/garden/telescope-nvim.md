---
title: Telescope.nvim
date: '2026-09-18'
lastmod: '2026-09-18'
draft: false
keywords:
- Telescope.nvim
- telescope
params:
  aliases:
  - telescope
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: New
    subcategories:
    - ide
---

[Telescope.nvim](https://github.com/nvim-telescope/telescope.nvim) is the fuzzy finder over lists for [[NeoVim]]. We **trial** it as the search surface in the editor config.

## Blurb

> telescope.nvim is a highly extendable fuzzy finder over lists. Built on the latest awesome features from neovim core.

## Summary

Use Telescope for file finding, live grep, buffers, help tags, and the other built-in pickers. It pairs with ripgrep for `live_grep` and `grep_string`, and with the LSP pickers for go-to-definition and references.

## Details

- **Upstream:** https://github.com/nvim-telescope/telescope.nvim
- **Role:** fuzzy finder in the [[NeoVim]] stack
- **Requirements:** NeoVim 0.11+ with LuaJIT; plenary.nvim
- **Nice to have:** ripgrep, fd, a native sorter extension
- **Related:** [[NeoVim]], [[which-key.nvim]]
