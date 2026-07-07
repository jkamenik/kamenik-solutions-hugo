---
title: Warp Terminal
date: '2026-06-30'
lastmod: '2026-07-02'
draft: false
keywords:
- Warp Terminal
- Warp ADE
params:
  aliases:
  - Warp ADE
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
    subcategories:
    - ide
---

[Warp Terminal](https://www.warp.dev/terminal). Is a Rust-based agentic development environment (ADE) born from the terminal.

## Summary

Warp Terminal is the desktop client for Denver Technologies' Warp stack. You get terminal mode and agent mode in one universal input, vertical session tabs, LSP-backed editing, and interactive diff review. It hosts the built-in [[Warp Agent]] and can wrap third-party CLI agents such as [[Claude Code]], [[Codex]], [[OpenCode]], and Gemini CLI with richer UI, notifications, and context sharing.

Choose it when you want agents inside a fast terminal shell rather than a VS Code fork. It pairs with [[Oz]] for cloud agents, schedules, triggers, and local-to-cloud handoff. The client is open source (`warpdotdev/warp`, AGPLv3) as of Apr 2026. Oz and Warp Drive backend remain proprietary.

## Details

- **Install:** https://www.warp.dev/download (macOS, Linux, Windows); Homebrew, winget, and distro packages per docs.
- **Surfaces:** terminal commands, agent conversations, file tree, inline code review, cloud-agent session join.
- **Third-party agents:** run Claude Code, Codex, OpenCode, and Gemini CLI inside Warp's agent toolbelt.
- **Team layer:** Warp Drive for shared workflows, rules, notebooks, and MCP configs across local and cloud agents.
- **Fit:** [[Tool]] / [[IDE]], agentic development environment with terminal form factor.
- **Contrast:** [[Cursor]] for our default VS Code-based editor stack; plain iTerm2 or Ghostty when you want a terminal without an ADE.
