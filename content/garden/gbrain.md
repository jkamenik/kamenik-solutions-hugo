---
title: "gbrain"
date: 2026-05-06
lastmod: 2026-05-17
draft: false

keywords:
  - gbrain
  - GBrain
  - Garry Tan Brain

params:
  garden:
    kind: item
    usefulness: trial
    category: technique
    movement: "No Change"
    subcategories:
      - ai-techniques
      - pkm

aliases:
  - /radar/techniques/gbrain
---

[gbrain](https://github.com/garrytan/gbrain) is Garry Tan's opinionated pattern for an LLM-maintained personal knowledge base. We rate it **trial**: the *ideas* are worth stealing—especially **two-layer pages** and **MECE directory resolvers**—but the full package is prescriptive (agent-maintains-everything, enrichment on every signal). Cherry-pick patterns and adapt them to your vault and workflows; do not treat gbrain as a religion.

## Blurb

> A personal intelligence system where your AI agent builds and maintains an interlinked wiki of everything you know — people, companies, deals, projects, meetings, ideas — as structured, cross-referenced markdown files. The agent writes and maintains all of it. You direct, curate, and think.

## Summary

**Worth applying:** pre-computed synthesis above a `---` separator with an append-only **Timeline** below; directory `README.md` resolvers that say what belongs where; one primary home per entity with wiki-links for adjacency.

**Take with skepticism:** blanket "enrichment fires on every signal," full automation of maintenance, and any rule that does not match how *you* file work (e.g. this vault uses [[PARA]] zones plus garden notes, not a single gbrain tree).

**This vault:** we **adopt** the two-layer pattern for research and garden notes ([[Agent Skills]], tech-garden items); we **assess** a root `RESOLVER.md` and always-on enrichment pipelines before copying them wholesale.

## Portable patterns (not dogma)

### Two-layer pages (compiled truth + timeline)

Above `---`: current synthesis—rewrite when facts change. Below `---`: append-only edit log (`**YYYY-MM-DD** | Author — …`). Subject-matter history belongs above the line; the timeline records *document* changes only.

### MECE directories (light touch)

Resolvers in zone `README.md` files help agents and humans file consistently. MECE applies to *directories*, not reality—use cross-links when entities span domains.

### Enrichment on every signal (optional)

Powerful for high-touch CRM-style brains; optional here. Prefer explicit jobs ([[Dagu]], morning briefing) over implicit always-on writes.

## Page template (adapt as needed)

```markdown
# Entity Name

> Executive summary — current state in one paragraph.

## State
- **Key field:** value

## Open Threads
- Active items (resolve → move detail to Timeline)

## See Also
- [[Linked page]]
