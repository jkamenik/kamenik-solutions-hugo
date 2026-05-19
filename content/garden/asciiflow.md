---
title: "AsciiFlow"
date: 2024-10-01
lastmod: 2026-05-18
draft: false

keywords:
  - AsciiFlow

params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: "No Change"
    subcategories:
      - diagramming

aliases:
  - /radar/tools/asciiflow
---

[AsciiFlow](https://asciiflow.com/) is a browser-based editor for drawing simple boxes-and-arrows diagrams as plain ASCII. We rate it **hold**: fine for a one-off sketch you paste into chat or a comment, but not for diagrams you expect to maintain. Use **[[Mermaid]]** (text in git) or **[[Draw.io]]** (formal visuals) instead.

## Blurb

> Draw ASCII diagrams in your browser.

## Summary

**When it helps:** quick architecture napkin sketches, Slack/PR comments, or README boxes where a PNG feels heavy and you already live in monospace.

**Why hold:** drawings are not structured source; resizing, diffs, and refactors are painful; output must render in a **monospace** font or alignment breaks; no real collaboration or export story compared to **[[Diagramming]]** tools you version-control.

**Graduate to:** **[[Mermaid]]** when the diagram should live in Markdown/docs and evolve with the repo; **[[Draw.io]]** when you need layers, icons, or shareable `.drawio` files.

## Details

| Topic | Notes |
|-------|--------|
| **Output** | Copy-paste ASCII; treat as disposable unless you snapshot it |
| **Rendering** | Test in target font (GitHub, terminal, email) before publishing |
| **Maintenance** | Manual edits only, no codegen from code or IaC |
