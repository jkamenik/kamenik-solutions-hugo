---
title: "tree-sitter"
date: 2026-04-15
lastmod: 2026-05-18
draft: false

keywords:
  - tree-sitter

params:
  garden:
    kind: item
    usefulness: assess
    category: code
    movement: "No Change"
    subcategories:
      - library

aliases:
  - /radar/code/tree-sitter
---

[Tree-sitter](https://tree-sitter.github.io/tree-sitter/) is an incremental parser generator and runtime that produces concrete syntax trees and updates them efficiently as source changes. We rate it **assess**: the default foundation when you are building editor features, multi-language tooling, or analyzers, but most product teams should consume it indirectly (via an editor or analyzer) rather than embed parsers themselves.

## Blurb

> Tree-sitter is a parser generator tool and an incremental parsing library. It can build a concrete syntax tree for a source file and efficiently update the syntax tree as the source file is edited.

## Summary

Unlike batch parsers that assume valid input, tree-sitter is designed for **interactive** use: partial parses stay useful, grammars are maintained per language, and the same core powers syntax highlighting in Neovim, Helix, GitHub, and Zed. You get fast, error-tolerant CSTs suitable for highlighting, structural search, and simple transforms.

When requirements grow into cross-node semantic graphs (data flow, control flow, security models), add [[tree-sitter-graph]] on top. For one language and a stable compiler front-end, a native parser or generator like ANTLR may be simpler than adopting the tree-sitter ecosystem.

## Details

- **Strengths:** incremental updates, robust parsing of incomplete code, broad grammar catalog, bindings for Rust/C/Node/Wasm/Python/Go and more.
- **Workflow:** define or reuse a grammar → generate parser → run queries (pattern match on syntax nodes) in your tool.
- **Typical uses:** editor syntax highlighting, code outline/folding, lightweight lint rules, test runners that need structure-aware selection.
- **Heavier uses:** static analysis pipelines, often paired with [[tree-sitter-graph]] (CodeQL-style stacks).
- **Category:** [[Code]] / [[Library]], a dependency you link, not a standalone service.
- **Pair with:** [[tree-sitter-graph]] when CST queries are not enough; contrast language-specific compiler APIs when you only target one language.
