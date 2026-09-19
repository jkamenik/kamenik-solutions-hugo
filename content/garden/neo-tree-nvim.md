---
title: neo-tree.nvim
date: '2026-09-18'
lastmod: '2026-09-19'
draft: false
keywords:
- neo-tree.nvim
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
    subcategories:
    - ide
---

[neo-tree.nvim](https://github.com/nvim-neo-tree/neo-tree.nvim) is the file and project tree plugin in the [[NeoVim]] stack. We **trial** it as the project management surface beside [[Telescope.nvim]] and [[which-key.nvim]].

## Blurb

> Neovim plugin to manage the file system and other tree like structures.

## Summary

Use neo-tree.nvim to browse the file system and keep project structure visible inside [[NeoVim]]. Open as a sidebar, floating window, or netrw-style split with `:Neotree`.

It has multiple sources: `filesystem`, `buffers`, `git_status`, and an experimental `document_symbols` view. It hijacks netrw so opening a directory shows the tree. Built on nui.nvim and plenary.nvim, it ships built-in git status and LSP diagnostics indicators.

## Details

- **Upstream:** https://github.com/nvim-neo-tree/neo-tree.nvim
- **Open:** `:Neotree` (left sidebar is the default)
- **Sources:** filesystem, buffers, git_status, document_symbols (experimental)
- **Dependencies:** nui.nvim, plenary.nvim
- **Related:** [[NeoVim]], [[Telescope.nvim]]
