---
title: cursor-agent
date: '2026-05-17'
lastmod: '2026-07-02'
draft: false
keywords:
- cursor-agent
- Cursor CLI
- Cursor Agent CLI
params:
  aliases:
  - Cursor CLI
  - Cursor Agent CLI
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: No Change
    subcategories:
    - ai-agent
---

[cursor-agent](https://cursor.com/cli). Is Cursor's terminal agent, TUI/CLI for running the same Cursor Agent in your shell, scripts, GitHub Actions, and headless automations, with frontier models and MCP.

## Blurb

> Built to help you ship, right from your terminal. Same commands, any environment.

## Summary

**Garden stance:** We **adopt** cursor-agent for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

- **Install:** `curl https://cursor.com/install -fsS | bash` (see Cursor CLI docs for npm and platform packages).
- **Auth:** Cursor subscription / team plan; CLI shares model access with the Cursor product.
- **Models:** Composer, Claude, GPT, Gemini, Grok, and other frontier models exposed in the CLI picker.
- **Automation:** headless mode and GitHub Actions integrations for doc updates, reviews, and custom agents.
- **Skills:** `.cursor/skills/` and rules; cross-reference [[Agent Skills - Sources]] for portable SKILL.md repos.
- **Fit:** [[Tool]] / [[AI Agent]], Cursor's agent runtime in the terminal ([[Cursor]] is the editor under [[IDE]]).
- **Contrast:** vendor-specific CLIs when not on Cursor; [[OpenCode]] for multi-provider open source.
