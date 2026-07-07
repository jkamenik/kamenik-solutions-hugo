---
title: Cursor
date: '2026-05-17'
lastmod: '2026-07-02'
draft: false
keywords:
- Cursor
- Cursor IDE
params:
  aliases:
  - Cursor IDE
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: No Change
    subcategories:
    - ide
---

[Cursor](https://cursor.com). Is a VS Code-based IDE with built-in AI: Tab completion, inline edit (Cmd+K), agent panel, and cloud agents.

## Blurb

> Built to make you extraordinarily productive, Cursor is the best AI coding agent.

## Summary

Cursor forks the VS Code experience and layers codebase indexing, model picker, rules, and `.cursor/skills/` on top. You can dial autonomy from Tab suggestions through targeted edits to full agent runs in the editor or via [[cursor-agent]] in the shell.

Choose Cursor when you want a single vendor for GUI + CLI agents. You get bring-your-own-model flexibility within their catalog and VS Code-compatible extensions without juggling separate CLIs per provider. It is an **editor platform** under [[IDE]]. The agent runtime in the terminal is [[cursor-agent]] under [[AI Agent]].

## Details

- **Install:** https://cursor.com/download (macOS, Windows, Linux); familiar VS Code layout and keybindings.
- **Auth:** Cursor Pro / Business / Enterprise subscription for models and agent features.
- **Models:** switch per task in the agent UI; Composer family plus major third-party models.
- **Features:** Tab model, inline edit, cloud agents, PR review (Bugbot), Slack/GitHub integrations per product docs.
- **Skills:** `.cursor/rules` and `.cursor/skills/`; portable SKILL.md repos in [[Agent Skills - Sources]].
- **Company:** [[Anysphere, Inc.|Anysphere]]
- **Fit:** [[Tool]] / [[IDE]], primary editor distribution (not the headless agent binary).
- **Contrast:** [[Claude Code]], [[Codex]], [[OpenCode]] when you want a non-Cursor agent hub; [[cursor-agent]] for the same stack in terminal/automation.
