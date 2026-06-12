---
title: "IDE"
date: 2026-05-17
lastmod: 2026-06-12
draft: false

keywords:
  - IDE

params:
  garden:
    kind: subcategory
    parent_category: tool
    subcategory_slug: ide
---

Under [[Tool]], **IDE** covers integrated development environments and editor platforms where you write, debug, and refactor code, often with LSP, terminals, and increasingly agent panels. This is the bounded workspace we prefer over always-on messaging agents: tools stay inside your repo and session policies.

Sibling subcategories include [[Provisioner]] (configure targets) and other [[Tool]] items. Tag a product here when the primary artifact is the editor or IDE distribution (VS Code, [[Cursor]], JetBrains, Neovim-as-IDE, Zed); not a plugin-only utility or a headless [[AI Agent]] gateway.

**Garden stance:** **adopt** [[Cursor]] for the editor; pair with **adopt** [[cursor-agent]] for terminal/CI agents in the same subscription.

Agent integration: many IDEs now host models via built-in chat or [[Agent Client Protocol]]; skills follow [[Agent Skills Framework]] when the runtime supports them. [[Dev Container]] often pairs with VS Code–class editors for reproducible dev environments.
