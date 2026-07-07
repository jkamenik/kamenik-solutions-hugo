---
title: OpenCode
date: '2026-05-17'
lastmod: '2026-07-02'
draft: false
keywords:
- OpenCode
- opencode-ai
params:
  aliases:
  - opencode-ai
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
    subcategories:
    - ai-agent
---

[OpenCode](https://opencode.ai). Is an open-source AI coding agent (terminal TUI, desktop app, and IDE extension) that connects to 75+ LLM providers (Claude, GPT, Gemini, local models, GitHub Copilot, ChatGPT accounts) with LSP-aware context and multi-session parallelism.

## Summary

**Garden stance:** We **trial** OpenCode for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

- **Install:** `curl -fsSL https://opencode.ai/install | bash`, `npm install -g opencode-ai`, Homebrew (`anomalyco/tap/opencode`), Docker image `ghcr.io/anomalyco/opencode`.
- **Auth:** Provider API keys via `/connect`, OpenCode Zen billing, or reuse ChatGPT Plus / GitHub Copilot logins where supported.
- **Models:** Any provider in the Models.dev directory; Zen subset for validated coding-agent performance.
- **Surfaces:** terminal (primary), desktop beta (macOS/Windows/Linux), IDE extension.
- **Fit:** [[Tool]] / [[AI Agent]], open, multi-model coding agent.
- **Contrast:** [[Cursor]] + [[cursor-agent]] for default IDE workflow; vendor CLIs when you stay in one ecosystem.
