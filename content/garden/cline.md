---
title: Cline
date: '2026-05-21'
lastmod: '2026-07-02'
draft: false
keywords:
- Cline
- Cline.bot
params:
  aliases:
  - Cline.bot
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - ai-agent
---

[Cline](https://cline.bot) is a tool we **assess** in the garden.

## Blurb

> Open-source AI coding agent with Plan/Act modes, MCP integration, and terminal-first workflows. Trusted by 8M+ developers worldwide.

## Summary

Cline (`cline/cline` on GitHub, 60k+ stars) runs as an IDE extension or headless CLI in your repo: coordinated edits, bash with live output, optional auto-approve, multi-agent teams with cron schedules, and integrations (Slack, Linear, GitHub Actions). Rules ship via `.clinerules`; skills and MCP extend tools. No vendor lock-in: Claude, GPT, Gemini, Bedrock, Azure, Vertex, Ollama, OpenRouter, and OpenAI-compatible endpoints.

Worth evaluating when you want a widely adopted, editor-agnostic open agent without switching IDEs, or when embedding agents via the SDK. Compare [[OpenCode]] for terminal-first multi-provider hubs; [[Kilo.ai]] for a similar VS Code + CLI story; [[Cursor]] when the editor platform and subscription are the anchor.

## Details

- **Install:** VS Code Marketplace / Open VSX (`saoudrizwan.claude-dev` legacy id → Cline); `npm i -g cline` for CLI; https://cline.bot/install
- **Docs:** https://docs.cline.bot
- **License:** Apache 2.0 (open source).
- **Models:** BYOK or local weights; all major cloud providers plus OpenAI-compatible APIs.
- **Surfaces:** IDE extension (VS Code, Cursor, Windsurf, VS Code Insiders), CLI, SDK (embed), JetBrains EA.
- **Features:** Plan/Act modes, checkpoints/undo, MCP, multi-agent coordinator, CI/Slack/Linear hooks.
- **Fit:** [[Tool]] / [[AI Agent]]: open, multi-surface coding agent.
- **Contrast:** [[OpenCode]] / [[Kilo.ai]] (peer open-source agents); [[Cursor]] + [[cursor-agent]] (default adopt stack).
