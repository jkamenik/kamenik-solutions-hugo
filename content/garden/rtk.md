---
title: "RTK"
date: 2026-05-27
lastmod: 2026-06-22
draft: false

keywords:
  - RTK
  - Rust Token Killer

params:
  aliases:
    - Rust Token Killer
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - ai-agent
aliases:
  - /radar/tools/rtk
---

[RTK](https://www.rtk-ai.app/) (Rust Token Killer) is an open-source CLI proxy that compresses shell command output before it reaches an [[AI Agent]] context window, typically cutting token use by 60-90% with transparent hooks for [[Claude Code]], [[Cursor]], and other coding assistants. We rate it **assess** under [[AI Agent]]: low-risk to try (MIT, single Rust binary, zero telemetry), but we have not validated savings or hook behavior in our own workflows yet.

## Blurb

> RTK compresses command outputs before they reach the context window. Better reasoning. Longer sessions. Lower costs.

## Summary

RTK sits between your agent and the shell. A PreToolUse-style hook rewrites commands like `git status` to `rtk git status` before execution; the model sees a compact summary instead of verbose boilerplate, progress bars, and repeated lines. Upstream reports ~89% average noise reduction across 2,900+ real commands (e.g. `cargo test` ~92%, `git status` ~81%, `find` ~78%).

Use when long agent sessions burn context on test runners, git diffs, linters, and container/k8s CLI output. `rtk init -g` wires [[Claude Code]] and Copilot; `rtk init -g --agent cursor` targets [[Cursor]]. `rtk gain` tracks per-command savings. Built-in agent tools (Read, Grep, Glob in Claude Code) bypass the hook unless you use shell equivalents or explicit `rtk read` / `rtk grep` calls.


## Details

- **Install:** `curl -fsSL https://raw.githubusercontent.com/rtk-ai/rtk/refs/heads/master/install.sh | sh`, Homebrew (`brew install rtk`), or `cargo install --git https://github.com/rtk-ai/rtk`.
- **Setup:** `rtk init -g` (Claude Code / Copilot), `rtk init -g --agent cursor` (Cursor), plus flags for Gemini, Windsurf, Cline, OpenCode, and others per [GitHub README](https://github.com/rtk-ai/rtk).
- **Analytics:** `rtk gain`, `rtk gain --graph`, `rtk discover` (commands that ran without RTK), `rtk session` (adoption rate).
- **License:** MIT; source at [github.com/rtk-ai/rtk](https://github.com/rtk-ai/rtk).
- **Scope:** 100+ commands across Git, Rust/Cargo, JS/TS, Python, Go, Docker, kubectl, and more.
- **Fit:** [[Tool]] / [[AI Agent]] adjunct, not a replacement for the agent runtime itself.
- **Contrast:** manual output truncation or narrower tool permissions; pairs with [[Claude Code]] and [[cursor-agent]] rather than competing with them.
