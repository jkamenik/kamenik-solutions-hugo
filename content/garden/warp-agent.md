---
title: Warp Agent
date: '2026-06-30'
lastmod: '2026-06-30'
draft: false
keywords:
- Warp Agent
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: New
    subcategories:
    - ai-agent
---

[Warp Agent](https://www.warp.dev/agents/warp-agent) is Warp's built-in multi-model coding agent. It runs inside [[Warp Terminal]] and on [[Oz]] with shared context, permission controls, and orchestration. We rate it **trial** under [[AI Agent]]: a capable bounded agent, but not our default. Interactive and headless work still favors [[cursor-agent]] with [[Cursor]] unless you are standardizing on the Warp stack.

## Blurb

> Code with a state of the art agent harness with multi-agent orchestration, model routing, access to all the best models, codebase indexing, and granular permission controls.

## Summary

Warp Agent drives an interactive agent loop in your repo: attach files, images, and URLs; run shell commands; review diffs inline; and track task lists across sessions. It supports multi-agent management, voice input, web search, and proactive fix recommendations from terminal output.

Use it when you already live in Warp Terminal or need the same harness locally and in Oz cloud runs. Oz can also run [[Claude Code]] and [[Codex]] as alternate harnesses under one control plane. Warp Agent is distinct from third-party CLIs that Warp hosts with a richer UI shell.

## Details

- **Surfaces:** embedded in [[Warp Terminal]]; cloud runs via [[Oz]] with one-click session join.
- **Models:** multi-model routing including frontier and open-weight options per Warp docs.
- **Context:** codebase indexing, Warp Drive rules, MCP servers, and WARP.md project steering files.
- **Controls:** autonomy settings, command allowlists, team permission policies, and audit logs on Oz.
- **Fit:** [[Tool]] / [[AI Agent]], Warp's native repo-bounded coding agent.
- **Contrast:** [[cursor-agent]] for our adopted Cursor stack; [[Claude Code]] and [[Codex]] when vendor billing or harness quality is the deciding factor.
