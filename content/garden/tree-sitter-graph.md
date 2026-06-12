---
title: "tree-sitter-graph"
date: 2026-04-15
lastmod: 2026-05-18
draft: false

keywords:
  - tree-sitter-graph

params:
  garden:
    kind: item
    usefulness: assess
    category: code
    movement: "No Change"
    subcategories:
      - library
---

[tree-sitter-graph](https://github.com/tree-sitter/tree-sitter-graph) is a Rust library and CLI that layers a **graph DSL** on top of [[tree-sitter]] parse trees, turning syntax nodes into arbitrary graphs with nodes, edges, and attributes. We rate it **assess**: essential when you are building static-analysis or IDE pipelines that need custom semantic graphs (GitHub uses it in the CodeQL stack), but overkill if you only need parsing or simple AST walks.

## Blurb

> The `tree-sitter-graph` library defines a DSL for constructing arbitrary graph structures from source code that has been parsed using tree-sitter.

## Summary

[[tree-sitter]] gives you fast, incremental concrete syntax trees; tree-sitter-graph adds **stanzas**, tree-sitter query patterns plus statements that emit graph nodes, link edges, and attach attributes. That separation lets tools map many languages through shared grammar work while encoding language-specific semantics in the graph rules (control flow, data flow, name resolution, etc.).

Typical consumers are security analyzers, linters with cross-file models, and language tooling that outgrows ad hoc AST visitors. You need comfort with tree-sitter queries and the graph DSL before committing; most application teams should depend on a finished analyzer rather than embed this directly.

## Details

- **Depends on:** [[tree-sitter]] parsers and grammars for each language you target.
- **Delivery:** Rust crate with optional CLI (`cargo install --features cli tree-sitter-graph`); graphs can serialize to JSON for downstream tools.
- **Mental model:** syntax nodes (from the parse) vs graph nodes (your derived model); stanzas bridge the two.
- **When to skip:** one-off scripts, simple formatters, or projects where [[tree-sitter]] alone plus hand-written visitors is enough.
- **Pair with:** [[tree-sitter]] (parser foundation); lives under [[Library]] in the [[Code]] category.
