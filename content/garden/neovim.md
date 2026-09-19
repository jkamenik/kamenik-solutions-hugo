---
title: NeoVim
date: '2026-09-18'
lastmod: '2026-09-18'
draft: false
keywords:
- NeoVim
- nvim
params:
  aliases:
  - nvim
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: New
    subcategories:
    - ide
---

[Neovim](https://neovim.io) is the hyperextensible Vim-based editor that won the editor slot in the TUI IDE stack. We **adopt** it for fast edits and file manipulation, not as an AI chat surface.

## Blurb

> Hyperextensible Vim-based text editor.

## Summary

Use NeoVim for fast edits and file manipulation while the coding agent lives in an [[OpenCode]] TUI inside a [[herdr]] pane. It won over the other terminal editors because it is extensible via [[Lua]] and has the best agent integration among TUI editors.

Key plugins in the stack: [[Telescope.nvim]] for fuzzy search, [[neo-tree.nvim]] for project management, and [[which-key.nvim]] for keybinding help.

The mental-model cost is Vim's verb-object order, inverted from [[Helix]]'s object-verb. Keep the config hand-rolled and minimal to avoid the maintenance tax that ruled out [[Emacs]].

## Details

- **Upstream:** https://neovim.io
- **Role:** terminal editor for fast edits and file manipulation
- **Config language:** [[Lua]] with `init.lua`
- **Stack plugins:** [[Telescope.nvim]], [[neo-tree.nvim]], [[which-key.nvim]]
- **Agent surface:** [[OpenCode]] TUI in a [[herdr]] pane; no in-editor chat panel
- **Related:** [[Vim]], [[Emacs]], [[Lua]], [[tree-sitter]]
