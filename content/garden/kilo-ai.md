---
title: "Kilo.ai"
date: 2026-05-21
lastmod: 2026-06-12
draft: false

keywords:
  - Kilo.ai
  - Kilo Code
  - KiloCode

params:
  aliases:
    - Kilo Code
    - KiloCode
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - ai-agent
---

[Kilo.ai](https://kilo.ai) (Kilo Code) is an open-source (Apache 2.0) AI coding agent for VS Code, JetBrains, CLI, and cloud surfaces. It offers specialized modes (Code, Architect, Debug, Ask, Custom), multi-model support (500+ via Kilo Gateway or BYOK), MCP, and cloud agents. We rate it **assess** under [[AI Agent]]: a credible open-source alternative in the same lane as [[OpenCode]] and IDE-bound agents, but not yet our default stack ([[Cursor]] + [[cursor-agent]] for daily work).

## Blurb

> The Open Source AI Coding Agent for VS Code, JetBrains, and your CLI. Build, ship, and iterate with any model, everywhere you work.

## Summary

Kilo Code (`kilocode.kilo-code` on VS Code / Open VSX) runs an agent loop in the editor or terminal: codebase-aware context, inline autocomplete, terminal and browser automation, code review, and human-in-the-loop controls. Kilo Auto offers a free tier without a credit card; paid tiers and BYOK cover model usage. A separate product, **KiloClaw**, is managed hosting for OpenClaw-style omnichannel agents (Telegram, Discord, Slack): outside the repo-bounded [[AI Agent]] sweet spot we prefer for coding workflows.

Worth evaluating when you want Apache-licensed, multi-surface agents with model portability and less vendor lock-in than a single IDE subscription. Compare [[OpenCode]] for terminal-first multi-provider hubs; [[Cursor]] when the editor platform is the anchor.

## Details

- **Install:** VS Code extension `kilocode.kilo-code`; JetBrains plugin; CLI; also on [Open VSX](https://open-vsx.org/extension/kilocode/kilo-code) for VS Code-compatible editors.
- **Docs:** https://kilo.ai/docs/getting-started
- **License:** Apache 2.0 (open source).
- **Models:** 500+ via Kilo Gateway (zero markup per marketing) or bring your own API keys.
- **Modes:** Code, Architect, Debug, Ask, plus custom modes.
- **Extras:** Cloud agents, MCP, leaderboard for model rankings, KiloClaw for hosted OpenClaw.
- **Fit:** [[Tool]] / [[AI Agent]]: open-source, multi-model coding agent.
- **Contrast:** [[OpenCode]] (similar open multi-provider story); [[Cursor]] + [[cursor-agent]] (default adopt stack); [[Claude Code]], [[Codex]], [[Gemini]] for single-vendor CLIs.
