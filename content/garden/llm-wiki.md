---
title: LLM Wiki
date: '2026-07-20'
lastmod: '2026-07-20'
draft: false
keywords:
- LLM Wiki
- Karpathy LLM Wiki
- LLM wiki pattern
params:
  aliases:
  - Karpathy LLM Wiki
  - LLM wiki pattern
  garden:
    kind: item
    usefulness: trial
    category: technique
    movement: New
    subcategories:
    - ai-techniques
---

[LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) is Andrej Karpathy's pattern for an LLM-maintained markdown knowledge base that compounds between queries instead of re-deriving answers via RAG. We **trial** it under **[[Technique]]** as the abstract idea behind agent-curated vaults like this one.

## Blurb

> A pattern for building personal knowledge bases using LLMs.

## Summary

**When to use:** You want knowledge to accumulate across sessions: ingest sources once, maintain entity and concept pages, and query a compiled wiki rather than raw RAG every time.

**When to skip:** One-shot Q&A over a fixed corpus is enough, or you will not keep sources and a schema (`AGENTS.md` / `CLAUDE.md`) under version control.

**Core loop:**

| Operation | Role |
|-----------|------|
| **Ingest** | Read a source; update summaries, entities, index, and log |
| **Query** | Answer from wiki pages; file good answers back as new pages |
| **Lint** | Find contradictions, orphans, stale claims, missing pages |

**Three layers:** immutable raw sources; LLM-owned wiki markdown; a schema doc that disciplines the agent.

**Vs related notes:** **[[gbrain]]** is an opinionated implementation of similar ideas. **[[Open Knowledge Format (OKF)]]** is an interchange spec that formalizes markdown knowledge bundles. This note is the pattern itself.

## Details

### Architecture (From the Gist)

1. **Raw sources** - curated, immutable inputs the agent reads but never edits.
2. **The wiki** - LLM-generated markdown (summaries, entities, concepts, synthesis). Humans read; the agent writes.
3. **The schema** - conventions and workflows in `AGENTS.md`, `CLAUDE.md`, or equivalent. Co-evolved with the agent.

### Indexing and Logging

- `index.md` - content catalog (links, one-line summaries, categories). Agent reads it first on query.
- `log.md` - append-only chronology of ingests, queries, and lint passes.

### Why It Differs From RAG

RAG rediscovers fragments on every question. An LLM wiki compiles once and keeps synthesis current: cross-links, contradictions, and topic pages are already maintained. Obsidian (or similar) is the IDE; the LLM is the programmer; the wiki is the codebase.

### Optional Tooling Called Out in the Gist

Local markdown search (e.g. qmd), Obsidian Web Clipper, graph view, Dataview over frontmatter, Marp for slides. All optional; the pattern stays file-based.
