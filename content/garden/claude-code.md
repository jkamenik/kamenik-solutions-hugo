---
title: "Claude Code"
date: 2026-05-17
lastmod: 2026-06-12
draft: false

keywords:
  - Claude Code

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "No Change"
    subcategories:
      - ai-agent
---

[Claude Code](https://docs.anthropic.com/en/docs/claude-code) is Anthropic's agentic coding assistant (terminal CLI, VS Code extension, and desktop surfaces) that reads your repo, edits files, runs commands, and follows project rules. We rate it **trial** under [[AI Agent]]: a strong bounded coding agent and the best fit when you live in the Anthropic stack and [[Agent Skills Framework]]. For day-to-day interactive work we usually reach for [[Cursor]] and the [[cursor-agent]] CLI instead (editor + agent in one place).

## Blurb

> Claude Code is an agentic coding tool that lives in your terminal, understands your codebase, and helps you code faster through natural language commands.

## Summary

Claude Code runs an agent loop in your project context: gather context (files, search, MCP), act (edit, bash, git), verify (tests, diffs). It supports hooks, subagents, plan mode, and the [[Agent Skills Framework]] directory layout used across this vault (`SKILL.md` files).

Use it for interactive development, refactors, and skill-driven workflows when Claude models or Anthropic billing are the constraint. It is a **repo-bounded** [[AI Agent]]; not an omnichannel personal bot. Always-on messaging gateways ([[OpenClaw]], [[hermes-agent|Hermes]]) are **hold** in this subcategory. For scheduled automation, prefer deterministic scripts and [[Dagu]] with LLM steps only where reasoning is required ([[projects/research/morning-briefing-personal-automation-platform]]).

Compare [[Codex]] for the same agent-loop-in-repo pattern on OpenAI plans.

## Details

- **Surfaces:** terminal (`claude` in repo root), [VS Code extension](https://code.claude.com/docs/en/vs-code), desktop app; pick one primary surface per machine.
- **Skills:** load from `.claude/skills/` or shared `agent-skills/` repos; see [[Agent Skills - Sources]] for curated lists.
- **Auth:** Claude subscription or Anthropic Console API; some surfaces allow third-party model routing.
- **Fit:** [[Tool]] / [[AI Agent]], agent-loop coding tool in the workspace (IDE surfaces are deployment options, not the taxonomy).
- **Contrast:** [[OpenClaw]] / Hermes for omnichannel bots; [[Cursor]] + [[cursor-agent]] for our default editor workflow; [[Codex]] on OpenAI plans.
