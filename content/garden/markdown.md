---
title: Markdown
date: '2026-08-24'
lastmod: '2026-08-24'
draft: false
keywords:
- Markdown
params:
  garden:
    kind: item
    usefulness: adopt
    category: language
    movement: No Change
---

[Markdown](https://daringfireball.net/projects/markdown/) is a lightweight markup language for creating formatted text using a plain-text syntax. We adopt it as the universal language for agent-maintained vaults and knowledge bases.

## Blurb

> Markdown is a text-to-HTML conversion tool for web writers. Markdown allows you to write using an easy-to-read, easy-to-write plain text format, then convert it to structurally valid XHTML (or HTML).

## Summary

**When to use:** Always use Markdown for agent-maintained vaults, documentation, and knowledge work - it's the universal lingua franca of plain-text formatting.

**When to skip:** Nearly never - avoid only when complex document layout or proprietary formatting is strictly required.

**Key trade-offs:**
- **Pros:** Simple syntax, human-readable, widely supported, converts cleanly to HTML, minimal lock-in
- **Cons:** Limited formatting vs. rich text, flavor inconsistencies, no single official standard (CommonMark helps)

**Related:** [[Obsidian]] [[SilverBullet]] [[PKM]] [[Lua]] [[YAML]] [[Frontmatter]]

## Details

| Topic | Notes |
|-------|--------|
| **Syntax** | Headers (#), lists (-), links ([text](url)), emphasis (*text*) |
| **Extensions** | Tables, task lists, footnotes, definition lists (via flavors) |
| **Flavors** | CommonMark, GitHub Flavored Markdown (GFM), Markdown Extra |
| **Processing** | Pandoc, marked, remark, showdown, various parsers |
| **Tooling** | Linters (markdownlint), formatters (prettier), converters (pandoc) |
| **Vault Use** | Native format for Obsidian, SilverBullet, Logseq, most PKM tools |
