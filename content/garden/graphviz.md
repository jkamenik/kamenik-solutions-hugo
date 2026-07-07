---
title: Graphviz
date: '2023-07-23'
lastmod: '2026-07-07'
draft: false
keywords:
- Graphviz
- DOT
- dot
params:
  aliases:
  - DOT
  - dot
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: No Change
    subcategories:
    - diagramming
---

[Graphviz](https://graphviz.org/) renders directed and undirected graphs from DOT text using layout engines such as `dot`, `neato`, and `fdp`. We **hold** it for legacy DOT pipelines. Prefer **[[Mermaid]]** for new docs-as-code diagrams.

## Blurb

> Graphviz is open source graph visualization software. Graph visualization is a way of representing structural information as diagrams of abstract graphs and networks.

## Summary

**What it is:** A CLI and library suite (originally AT&T Labs) that turns DOT language files into PNG, SVG, PDF, and other outputs. Strong at automatic layout of node-edge graphs. Weak at modern software diagram types and author ergonomics compared to **[[Mermaid]]**.

**When to use (hold, not banned):**

| Situation | Notes |
|-----------|--------|
| Existing DOT in repos or CI | Maintain what you have; do not rewrite without cause |
| Tools that emit DOT | `terraform graph`, profilers, codegen, or analysis pipelines |
| Large abstract graphs | `fdp` / `sfdp` layouts for hundreds of nodes where Mermaid chokes |
| Library embedding | Apps that call Graphviz C APIs for programmatic layout |

**When to skip (default for new work):**

- Architecture docs in Markdown, ADRs, or Hugo posts (**[[Mermaid]]** **adopt**)
- Stakeholder polish, cloud icons, manual layout (**[[Draw.io]]** **trial**)
- Disposable chat sketches (**[[AsciiFlow]]** **hold**)

**Trade-offs:** DOT is verbose. Default styling looks dated. Custom icons often need HTML-like labels or post-processing. Scope is graphs and digraphs only. No native sequence, ER, or Gantt diagram types.

## Details

### DOT Language and Layout Engines

| Engine | Best for |
|--------|----------|
| `dot` | Hierarchical directed graphs (layered layouts) |
| `neato` | Undirected graphs; spring-model layouts up to ~1k nodes |
| `fdp` | Force-directed layouts for medium undirected graphs |
| `sfdp` | Multiscale `fdp` for large graphs |
| `circo` | Circular layouts for cyclic structures |
| `twopi` | Radial layouts from a root node |

Author a `.gv` or `.dot` file, then run `dot -Tsvg input.gv -o output.svg`. Other binaries (`neato`, `fdp`, etc.) share the same DOT input with different layout algorithms.

### Output and Integration

| Topic | Notes |
|-------|--------|
| **Formats** | PNG, SVG, PDF, PS, plain text, JSON-like graph dumps |
| **Obsidian / Hugo** | No first-class DOT fence; render to SVG and embed, or use a plugin |
| **GitHub** | No native DOT preview in Markdown (unlike **[[Mermaid]]**) |
| **Libraries** | C core with bindings in many languages for programmatic graph build |

### Compared to **[[Mermaid]]**

| Topic | Graphviz | Mermaid |
|-------|----------|---------|
| Diagram types | Graphs and digraphs | Flowchart, sequence, class, ER, Gantt, and more |
| Author UX | Low-level attributes and layout tuning | Markdown-adjacent blocks in docs |
| Git / PR diffs | Works if DOT is source | **Adopt** default for repo-native diagrams |
| Visual polish | Dated defaults; heavy styling effort | Cleaner defaults for software docs |
| Garden stance | **hold** | **adopt** |

See **[[Diagramming]]** for the full garden matrix.

### References

- [Graphviz documentation](https://graphviz.org/documentation/)
- [DOT language](https://graphviz.org/doc/info/lang.html)
- [Drawing graphs with dot (PDF guide)](https://graphviz.org/pdf/dotguide.pdf)
