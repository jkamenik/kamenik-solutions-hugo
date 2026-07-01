---
title: Termdock
date: '2026-07-01'
lastmod: '2026-07-01'
draft: false
keywords:
- Termdock
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: New
    subcategories:
    - ide
---

[Termdock](https://www.termdock.com/en) is a terminal-centric AI development environment for macOS and Windows. It unifies multi-project workspaces, split terminals, Tree-sitter code search, and AI CLI tooling in one local-first desktop app. We **assess** it because the public download is still marked coming soon and we have not run it against our repos. It sits under [[IDE]] as a [[Warp Terminal]]-class alternative when you want project-aware terminals instead of a VS Code fork like [[Cursor]].

## Blurb

> Ten terminals is not a workflow.

## Summary

Termdock targets developers juggling many repos and CLI tools at once. Each workspace gets its own root directory, terminal tabs, and Git state. You can split up to four terminals on one screen, drag files or images into any shell, and jump between projects without losing context.

Built-in Tree-sitter search spans 13 languages for definitions, references, and call graphs without grep. The app also ships a Monaco editor, file tree with preview, Git blame and branch views, prompt templates, and session restore after restarts.

v1.6 adds agent-controlled terminals through a local HTTP API with cursor-based output streaming. It also supports remote control via Discord and Telegram bots. Pricing is free according to the product schema on the site.

## Details

### App Profile

| Field | Value |
|-------|-------|
| Category | [[Tool]] / [[IDE]] |
| Platforms | macOS, Windows (site lists Linux as supported; homepage notes other platforms coming soon) |
| License / price | Free (per site schema) |
| Upstream | https://www.termdock.com/en |
| GitHub | https://github.com/termdock |
| Releases | https://github.com/termdock/termdock-issues/releases |

### Core Capabilities

- **Workspaces:** 10+ independent project contexts with per-repo Git status.
- **Layout:** Multi-terminal splits, picture-in-picture, drag-and-drop paths into any CLI (`curl`, `ffmpeg`, `git`, etc.).
- **Code intelligence:** Tree-sitter AST search across 13 languages; built-in Monaco editor.
- **Files and Git:** File tree, preview, full-text search, Git visualization and blame.
- **Agents:** Local HTTP API for agent-controlled terminal sessions; Discord and Telegram remote control (v1.6).
- **Local-first:** Works offline; no plugin stack required per marketing.

### Fit and Contrast

- **Choose Termdock** when terminal-native multi-repo workflows matter more than an IDE shell.
- **Compare [[Warp Terminal]]** for a mature agentic terminal ADE with open-source client and third-party harness wrapping.
- **Compare [[Cursor]]** when LSP-heavy editing and our default agent stack should stay inside a VS Code fork.
- **Roadmap items** on the site include an AI work agent and deeper code search marked coming soon.
