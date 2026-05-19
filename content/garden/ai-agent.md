---
title: "AI Agent"
date: 2026-04-20
lastmod: 2026-05-18
draft: false

keywords:
  - AI Agent

params:
  garden:
    kind: subcategory
    parent_category: tool
    subcategory_slug: ai-agent

aliases:
---

Under [[Tool]], **AI Agent** covers runnable agent **tools**, services that run an agent loop (observe context → plan → call tools → persist state) rather than one-shot chat completions. You install or self-host them and build workflows on top, often via [[Agent Skills]] and protocols like [[Agent Client Protocol]].

**In this subcategory:** repo-bounded coding agents such as [[cursor-agent]], [[Claude Code]], [[Codex]], [[Gemini]], and [[OpenCode]] (terminal/IDE surfaces are how you run them; the product is the agent loop, not the editor distribution). **Not here:** raw model runtimes like [[Ollama]] ([[Platform]]); editor shells without an agent runtime under [[IDE]]; broad [[Artificial Intelligence & Machine Learning]] techniques.

**Garden stance:** omnichannel personal agents ([[hermes-agent|Hermes]], [[OpenClaw]]) are **hold** / **Moved Out**; hard to secure across machines ([[ADR-0003-each-machine-runs-pipelines-independently]]). **Adopt** [[cursor-agent]] (with [[Cursor]]) for daily work; other bounded coding agents are **trial** when another vendor or open-source hub fits better.

Tag an item here when the core value is an agent with tools, sessions, and autonomous or semi-autonomous action; not just an editor without an agent runtime.
