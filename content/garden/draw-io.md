---
title: "Draw.io"
date: 2024-10-01
lastmod: 2026-06-12
draft: false

keywords:
  - Draw.io
  - diagrams.net
  - drawio

params:
  aliases:
    - diagrams.net
    - drawio
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "No Change"
    subcategories:
      - diagramming
aliases:
  - /radar/tools/draw-io
---

[Draw.io](https://www.diagrams.net/) (diagrams.net) is a browser and desktop diagram editor for architecture sketches, flowcharts, network layouts, and C4-style views. We rate it **trial** under **[[Diagramming]]**: use when **[[Mermaid]]** (**adopt**) is not enough for polish, icons, or manual layout; commit `.drawio` source and exported SVG/PNG in the repo when the diagram must last.

## Blurb

> diagrams.net is a free online diagram software for making flowcharts, process diagrams, org charts, UML, ER and network diagrams.

## Summary

**What you get:** drag-and-drop canvas, shape libraries (AWS/Azure/GCP icons, UML, BPMN), layers, and exports (PNG, SVG, PDF). Files are XML (`.drawio` or `.drawio.xml`) you can store next to docs.

**When trial fits:**

| Use | Notes |
|-----|--------|
| **Stakeholder decks** | Polished boxes-and-arrows for reviews |
| **Complex layout** | Fine-grained positioning Mermaid fights |
| **Icon-heavy architecture** | Cloud vendor stencils out of the box |
| **VS Code / Cursor** | [Draw.io Integration](https://marketplace.visualstudio.com/items?itemName=hediet.vscode-drawio) edits files in-repo |

**When to prefer Mermaid instead:**

- Diagram lives in Markdown, ADRs, or Hugo and should **diff cleanly** in PRs
- Sequence/flowchart/class diagrams with low layout friction
- CI or docs site renders diagrams from text (no binary/XML churn)

**Why not adopt (yet):** XML merges are noisier than text; easy to fork "pretty" diagrams that drift from code; temptation to screenshot instead of exporting source.

## Details

| Topic | Notes |
|-------|--------|
| **Storage** | Commit `.drawio` + optional `diagram.png` for readers who do not open the editor |
| **Desktop** | [Desktop app](https://github.com/jgraph/drawio-desktop) for offline or large files |
| **Integrations** | Google Drive, OneDrive, GitHub; pick one backing store per team to avoid link rot |
| **Security** | Self-host or use desktop app if diagrams are sensitive; default web app is third-party hosted |
| **Graduate from** | **[[AsciiFlow]]** (**hold**) for anything you will maintain |

**References**

- [diagrams.net](https://www.diagrams.net/)
- [Draw.io VS Code extension](https://marketplace.visualstudio.com/items?itemName=hediet.vscode-drawio)
