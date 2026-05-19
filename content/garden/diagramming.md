---
title: "Diagramming"
date: 2026-01-08
lastmod: 2026-05-18
draft: false

keywords:
  - Diagramming
  - diagrams
  - diagram tools

params:
  garden:
    kind: subcategory
    parent_category: tool
    subcategory_slug: diagramming

aliases:
---

Under **[[Tool]]**, **Diagramming** groups products and formats for **visual models** of software: architecture, flows, sequences, ER diagrams, and deployment sketches. Prefer diagrams that **live in Git** (text or structured XML) over screenshots that rot.

**In this subcategory:**

| Tool | Rating | Use when |
|------|--------|----------|
| **[[Mermaid]]** | **adopt** | Markdown/docs, PRs, Hugo; sequence, flowchart, class, C4-style in repo |
| **[[Draw.io]]** | **trial** | Rich layouts, icons, `.drawio` in repo, VS Code/Cursor extension |
| **[[Graphviz]]** | **hold** | Legacy DOT pipelines only; prefer Mermaid for new text diagrams |
| **[[AsciiFlow]]** | **hold** | Disposable chat/comment sketches only |

**Not here:** whiteboard photos; slide-deck-only graphics; **[[OpenAPI]]** specs (source of truth for APIs, diagrams are derived); screenshot tools.

**Garden stance:**

- **Adopt** **[[Mermaid]]** in `README`, ADRs, **[[gbrain]]** research pages, and blog posts so diagrams diff with code.
- **Trial** **[[Draw.io]]** (diagrams.net) when stakeholders need polish or manual layout; store `.drawio` + export PNG/SVG in the repo if published.
- **Hold** one-off ASCII art (**[[AsciiFlow]]**) and new **[[Graphviz]]** unless you already depend on DOT.

**Practices:**

- Diagram **to explain**, not to decorate; one diagram per question.
- Link diagrams from the doc that owns the decision (ADR, design note).
- For C4 or architecture overviews, start at context/container level; drill down in separate files.

**How to tag:** **[[Tool]]** items with `subcategories: ["[[Diagramming]]"]` when the product's main job is drawing or rendering diagrams.
