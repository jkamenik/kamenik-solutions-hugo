---
title: CodexBar
date: '2026-06-28'
lastmod: '2026-06-30'
draft: false
keywords:
- CodexBar
params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: New
    subcategories:
    - ai-agent
---

[CodexBar](https://github.com/steipete/CodexBar) is a macOS menu-bar app and CLI that surfaces AI coding-provider usage windows, credit balances, reset countdowns, and local token-cost estimates across Codex, Claude, Cursor, Gemini, and many other providers. We **adopt** it for day-to-day token budgeting and model-switch decisions. Pair with agent workflows where subscription limits and per-model cost vary.

## Blurb

> Tiny macOS 14+ menu bar app that keeps AI coding-provider limits visible and shows when each window resets. Plan around resets, credits, spend, and cost scans. Privacy-first: reuses existing provider sessions so no passwords are stored.

## Summary

CodexBar tracks per-provider session, weekly, and monthly usage windows with countdowns to the next reset. It also runs local cost scans from conversation logs (`codexbar cost --provider codex`, `claude`, or `both`) when API billing detail is unavailable. Estimates are API-equivalent, not exact subscription charges.

Use when you run multiple coding agents and need visibility before starting a long task. The bundled CLI supports scripts and CI on macOS and Linux. Contrast [[RTK]], which compresses shell output before it hits the context window; CodexBar measures spend and limits after the fact.

## Details

- **Install:** `brew install --cask steipete/tap/codexbar` or GitHub Releases; Sparkle auto-updates on macOS.
- **CLI:** `codexbar cost` analyzes local Claude and Codex history offline; returns session and 30-day token and USD estimates.
- **Providers:** Codex, OpenAI, Claude, Cursor, Gemini, Copilot, OpenRouter, LiteLLM proxy, Vertex AI, AWS Bedrock, and others per upstream docs.
- **Caveats:** Local cost figures are estimates from published pricing and local logs; flat-rate plans may not match billed amounts.
- **Fit:** [[Tool]] / [[AI Agent]] ops layer for cost discipline and model routing decisions.
