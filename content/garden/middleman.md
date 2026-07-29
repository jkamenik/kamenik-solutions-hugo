---
title: Middleman
date: '2024-10-01'
lastmod: '2026-07-28'
draft: false
keywords:
- Middleman
- Middleman App
params:
  aliases:
  - Middleman App
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
---

[Middleman](https://middlemanapp.com/) is a **[[Ruby]]** static-site generator with flexible templates, data files, asset processing, and extension support. We **assess** it for inherited Ruby documentation sites or teams already committed to that ecosystem.

## Blurb

> Hand-crafted frontend development

## Summary

**When to use:** Maintain an existing Middleman site, or build a content site where Ruby, ERB, Haml, Sass, and custom extensions match the team's skills. It remains maintained, with version 4.6.3 released in February 2026.

**When to skip:** Starting a new documentation site without a Ruby requirement. More common static-site ecosystems offer broader themes, integrations, and contributor familiarity.

**Why it is here:** HashiCorp historically used Middleman for documentation. That makes it useful context when examining older HashiCorp documentation repositories, but not an automatic recommendation for new work.

## Details

| Topic | Notes |
|-------|--------|
| **Runtime** | Ruby gem; projects use Bundler and a `config.rb` configuration file |
| **Content** | Supports ERB, Haml, Slim, Markdown, YAML data, Sass, and other frontend tools |
| **Workflow** | `middleman server` for local development; `middleman build` for static output |
| **Status** | Long-lived MIT project with active 4.6.x maintenance through 2026 |

**References**

- [Middleman documentation](https://middlemanapp.com/basics/getting-started/)
- [middleman/middleman on GitHub](https://github.com/middleman/middleman)
- [Middleman on RubyGems](https://rubygems.org/gems/middleman)
