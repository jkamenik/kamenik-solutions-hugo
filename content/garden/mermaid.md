---
title: Mermaid
date: '2023-07-23'
lastmod: '2026-07-07'
draft: false
keywords:
- Mermaid
params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: No Change
    subcategories:
    - diagramming
---

[Mermaid](https://mermaid.js.org/) is a JavaScript library that renders Markdown-inspired text into flowcharts, sequence diagrams, ER diagrams, and more. We **adopt** it for git-backed docs, ADRs, research pages, and Hugo posts where diagrams should diff in PRs.

## Blurb

> JavaScript based diagramming and charting tool that renders Markdown-inspired text definitions to create and modify diagrams dynamically.

## Summary

**When to use:**

| Use | Notes |
|-----|--------|
| **Markdown and Hugo** | Fenced `mermaid` blocks render in many static sites and Git hosts |
| **Architecture docs** | Flowcharts, sequence, class, C4-style, and ER views in repo text |
| **Living research** | **[[gbrain]]** pages and ADRs where the diagram evolves with prose |
| **Quick reviews** | [Mermaid Live Editor](https://mermaid.live/) for paste-and-share drafts |

**When to skip:**

- Fine-grained layout, layers, or cloud icon libraries (**[[Draw.io]]** trial fits better)
- Legacy DOT pipelines you already maintain (**[[Graphviz]]** hold)
- One-off chat sketches that will never be committed (**[[AsciiFlow]]** hold)

**Trade-offs:** Syntax is learnable but strict. Typos break renders. Layout is automatic, so dense diagrams can get crowded. Prefer small, focused diagrams over kitchen-sink canvases.

## Details

### Diagram Types

| Declaration | Diagram type |
|-------------|--------------|
| `flowchart` / `graph` | Flowchart |
| `sequenceDiagram` | Sequence diagram |
| `classDiagram` | Class diagram |
| `erDiagram` | Entity relationship |
| `stateDiagram-v2` | State diagram |
| `gantt` | Gantt chart |
| `gitGraph` | Git graph |
| `mindmap` | Mindmap |
| `timeline` | Timeline |
| `quadrantChart` | Quadrant chart |

Every diagram starts with a type declaration, then node and edge definitions. Line comments use `%%`.

### Deployment

| Topic | Notes |
|-------|--------|
| **npm / CDN** | `mermaid` package or jsDelivr for browser rendering |
| **GitHub** | Native Mermaid in Markdown (README, issues, PR bodies) |
| **Hugo** | Goldmark or dedicated shortcode; this site's garden pages support fenced blocks |
| **Obsidian** | Core Mermaid plugin renders fenced blocks in preview |

### Syntax Tips

- Wrap reserved words like `end` in quotes when they appear as node labels.
- Avoid `{}` inside `%%` comments; the parser can confuse them with directives.
- Test in [Mermaid Live Editor](https://mermaid.live/) before committing complex syntax.

### Compared to Alternatives

| Tool | When Mermaid wins | When the alternative wins |
|------|-------------------|---------------------------|
| **[[Draw.io]]** | Text diffs, docs-as-code, CI-rendered Markdown | Manual layout, vendor icon stencils, stakeholder polish |
| **[[Graphviz]]** | Broader diagram types, simpler author UX for common software diagrams | Existing DOT tooling or graph algorithms you already depend on |

See **[[Diagramming]]** for the full garden matrix.

**References**

- [Mermaid documentation](https://mermaid.js.org/)
- [Mermaid Live Editor](https://mermaid.live/)
- [npm: mermaid](https://www.npmjs.com/package/mermaid)
