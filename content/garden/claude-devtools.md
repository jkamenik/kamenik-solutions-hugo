---
title: Claude DevTools
date: '2026-07-06'
lastmod: '2026-07-07'
draft: false
keywords:
- Claude DevTools
- claude-devtools
params:
  aliases:
  - claude-devtools
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: New
    subcategories:
    - ai-agent
---

[Claude DevTools](https://claude-dev.tools/) is a local desktop app that reads Claude Code session logs from `~/.claude/` and restores tool calls, thinking steps, and context breakdown the terminal hides. We **trial** it for post-session debugging, subagent review, and copy-friendly transcript inspection.

## Blurb

> Your Claude is coding blind.

## Summary

**When to use:**

- After Claude Code v2.1.20+ collapsed terminal output into opaque summaries
- Inspecting Read/Edit/Bash I/O and subagent trees
- Per-turn context attribution (CLAUDE.md, skills, `@`-mentions, tool output)
- Cross-session search or SSH remote session review
- Alerting on sensitive file access or high token use

**When to skip:** aggregate cost dashboards and quota progress bars (use [[Claude Usage]] or [[CodexBar]]); sessions with no local JSONL (Cowork); replacing `--verbose` when you only need a one-off raw dump.

**Trade-offs:** MIT desktop app (macOS Homebrew cask, Windows `.exe`, Linux AppImage, Docker self-host). Reads disk only. No login, API keys, or outbound calls. Works on historical sessions from any tool that wrote `~/.claude/` logs.

## Details

| Topic | Notes |
|-------|--------|
| **Site** | [claude-dev.tools](https://claude-dev.tools/) |
| **Repo** | [matt1398/claude-devtools](https://github.com/matt1398/claude-devtools) (MIT, TypeScript, ~3.7k stars) |
| **Install** | `brew install --cask claude-devtools`; or GitHub Releases (.dmg, .exe, AppImage); Docker self-host |
| **Data source** | Read-only access to `~/.claude/` session JSONL already on disk |
| **Not a wrapper** | Does not hook or modify Claude Code; parses existing logs |

**Key features:**

- **Context reconstruction:** per-turn token attribution across seven categories with compaction visualization
- **Tool call inspector:** syntax-highlighted reads, inline edit diffs, bash output, nested subagent trees
- **Project memory pane:** browse `~/.claude/projects/` memory layers with in-app search and "Open in…" launchers
- **Notification triggers:** regex alerts for sensitive paths, tool errors, token thresholds
- **SSH remote sessions:** inspect logs on remote hosts via `~/.ssh/config`
- **Command palette:** Cmd+K cross-session search with snippet highlights
- **Multi-pane layout:** compare sessions side by side

**Fit:** [[Tool]] / [[AI Agent]] debugging layer for [[Claude Code]]. Complements [[Claude Usage]] (charts and cost totals) and [[CodexBar]] (provider quota windows).
