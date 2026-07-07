---
title: Claude Usage
date: '2026-07-06'
lastmod: '2026-07-07'
draft: false
keywords:
- Claude Usage
- Claude Code Usage Dashboard
params:
  aliases:
  - Claude Code Usage Dashboard
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: New
    subcategories:
    - ai-agent
---

[Claude Usage](https://github.com/phuryn/claude-usage) is a local Python dashboard and CLI that scans Claude Code JSONL logs under `~/.claude/` and charts tokens, models, costs, and session history. We **trial** it when you want subscription-window visibility that Anthropic's UI does not expose.

## Blurb

> Pro and Max subscribers get a progress bar. This gives you the full picture.

## Summary

**When to use:** daily or weekly Claude Code spend reviews; comparing model mix across projects; Pro/Max quota tracking with progress bars; terminal summaries (`today`, `week`, `stats`) without opening a browser.

**When to skip:** deep per-turn debugging (use [[Claude DevTools]]); Cowork sessions (server-side, no local JSONL); multi-provider dashboards ([[CodexBar]] covers Claude plus Codex, Cursor, Gemini, and others from the menu bar).

**Trade-offs:** Python stdlib only (no pip deps), incremental SQLite scan, Homebrew/uv/Docker install paths, and an optional VS Code extension. Cost figures are estimates from local logs and published pricing, not exact invoices.

## Details

| Topic | Notes |
|-------|--------|
| **Upstream** | [phuryn/claude-usage](https://github.com/phuryn/claude-usage) (MIT, ~2k stars, Python) |
| **Data source** | Local JSONL under `~/.claude/` from Claude Code CLI, VS Code extension, and dispatched Code sessions |
| **Not captured** | Cowork sessions (server-side, no local transcripts) |
| **Surfaces** | Web dashboard (`claude-usage dashboard`), CLI subcommands, VS Code extension |
| **Install** | `brew tap phuryn/claude-usage && brew install phuryn/claude-usage/claude-usage`; or `uv tool install git+https://github.com/phuryn/claude-usage`; or clone + `python3 cli.py dashboard` |
| **Database** | Incremental scan into `~/.claude/usage.db` (SQLite) |
| **Companion** | [burnstop](https://github.com/phuryn/burnstop) (same author ecosystem) |

**CLI quick reference:**
```bash
claude-usage scan          # populate usage.db from JSONL
claude-usage today         # today's usage by model
claude-usage week          # last 7 days
claude-usage stats         # all-time stats
claude-usage dashboard     # browser UI (default localhost:8080)
```

**Fit:** [[Tool]] / [[AI Agent]] ops layer alongside [[Claude Code]]. Pairs with [[CodexBar]] when you need cross-provider menu-bar limits; pairs with [[Claude DevTools]] when you need session forensics, not aggregate charts.
