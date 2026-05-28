---
title: "Cursor"
date: 2026-05-17
lastmod: 2026-05-21
draft: false

keywords:
  - Cursor
  - Cursor IDE

params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: "New"
    subcategories:
      - ide

aliases:
  - /radar/tools/cursor
---

[Cursor](https://cursor.com) is a VS Code–based IDE with built-in AI: Tab completion, inline edit (Cmd+K), agent panel, and cloud agents, on a paid Cursor subscription with access to many frontier models (Composer, Claude, GPT, Gemini, Grok, and more). Built by [[Anysphere]]. We **adopt** it under [[IDE]] as our default editor stack: one simple ecosystem for multi-model coding when paired with [[cursor-agent]] for terminal and CI workflows.

## Blurb

> Built to make you extraordinarily productive, Cursor is the best way to code with AI.

## Summary

Cursor forks the VS Code experience and layers codebase indexing, model picker, rules, and `.cursor/skills/` on top. You can dial autonomy from Tab suggestions through targeted edits to full agent runs in the editor or via [[cursor-agent]] in the shell.

Choose Cursor when you want a single vendor for GUI + CLI agents, bring-your-own-model flexibility within their catalog, and VS Code–compatible extensions without juggling separate CLIs per provider. It is an **editor platform** under [[IDE]], the agent runtime in the terminal is [[cursor-agent]] under [[AI Agent]].

## Details

- **Install:** https://cursor.com/download (macOS, Windows, Linux); familiar VS Code layout and keybindings.
- **Auth:** Cursor Pro / Business / Enterprise subscription for models and agent features.
- **Models:** switch per task in the agent UI; Composer family plus major third-party models.
- **Features:** Tab model, inline edit, cloud agents, PR review (Bugbot), Slack/GitHub integrations per product docs.
- **Skills:** `.cursor/rules` and `.cursor/skills/`; portable SKILL.md repos in [[Agent Skills - Sources]].
- **Company:** [[Anysphere]] (Anysphere, Inc.)
- **Fit:** [[Tool]] / [[IDE]], primary editor distribution (not the headless agent binary).
- **Contrast:** [[Claude Code]], [[Codex]], [[OpenCode]] when you want a non-Cursor agent hub; [[cursor-agent]] for the same stack in terminal/automation.
