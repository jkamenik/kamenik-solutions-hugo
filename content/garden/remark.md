---
title: Remark
date: '2024-10-01'
lastmod: '2026-07-29'
draft: false
keywords:
- Remark
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
    subcategories:
    - presentation
---

[Remark](https://remarkjs.com) is an in-browser Markdown slideshow: one HTML file, CSS, and JS. We **trial** it under **[[Presentation]]** when slides should live in Git as plain text instead of PowerPoint or Keynote.

## Blurb

> A simple, in-browser, Markdown-driven slideshow tool targeted at people who know their way around HTML and CSS.

## Summary

**What it is:** Browser-rendered decks from Markdown. Slide breaks are `---` lines. Presenter mode, clone view, syntax highlighting, and CSS-based styling.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Info-heavy talks | Text, images, and Mermaid with low tooling overhead |
| Tech talks in Git | Version slides next to the code you demo |
| Offline / simple hosting | Single HTML file; Dropbox or GitHub Pages |
| Custom look | Style with normal CSS and content classes |

**When to skip:**

- Non-technical authors who need WYSIWYG slide apps
- Heavy animation or corporate template lock-in
- Teams already standardized on Reveal.js or Marp with shared themes

**Trade-offs:** Low effort when the deck is mostly information, not spectacle. Layout power is CSS skill, not a slide designer. Project is mature and quiet; expect DIY maintenance.

## Details

### Slide Properties

Initial key-value lines on a slide become properties:

- `name` and `class` for naming and styling
- `template` and `layout` for reuse
- `{{ property }}` expands to property values

See the [slide properties wiki](https://github.com/gnab/remark/wiki/Markdown#slide-properties).

### Other Extensions

- Content classes: `.footnote[.red[*] note]` wraps spans with CSS classes
- Fenced code blocks with language tags for highlighting
- `???` separates slide body from presenter notes (`P` toggles presenter mode; `C` clones the view)

**References**

- [remarkjs.com](https://remarkjs.com)
- [gnab/remark](https://github.com/gnab/remark)
