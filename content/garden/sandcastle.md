---
title: Sandcastle
date: '2026-08-14'
lastmod: '2026-08-14'
draft: false
keywords:
- Sandcastle
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: New
    subcategories:
    - ai-agent
---

[Sandcastle](https://github.com/mattpocock/sandcastle) is a TypeScript library for orchestrating AI coding agents in isolated sandboxes. You invoke agents with a single `sandcastle.run()`, and it handles sandboxing, branch strategy, and merging commits back. We **assess** it for parallelizing AFK coding agents in our own repos.

## Blurb

> A TypeScript library for orchestrating AI coding agents in isolated sandboxes.

## Summary

**What it is:** A provider-agnostic orchestrator that runs coding agents (Claude Code, Codex, and more) inside isolated sandboxes. Built-in providers cover Docker, Podman, and Vercel, plus a no-sandbox option. A configurable branch strategy controls how agent commits land, from writing directly to the working tree to merging from a dedicated branch.

**When to use:** You want to run multiple AFK agents in parallel, build review pipelines, or orchestrate your own coding agents safely without touching the host working tree.

**When to skip:** Single interactive agent sessions where a plain IDE panel or terminal already suffices. You need tight control-plane policy enforcement rather than sandbox orchestration.

**Key features:** `sandcastle.run()` one-shot API, `createSandbox()` for reuse across runs, `createWorktree()` for independent worktrees, three branch strategies (head, merge-to-head, branch), structured output with schema validation, prompt templating with `{{KEY}}` and `` !`command` `` expansion, and lifecycle hooks. MIT licensed.

## Details

**Package:** `@ai-hero/sandcastle`

**Sandbox providers:** Docker, Podman, Vercel (`@vercel/sandbox`), no-sandbox, plus custom via `createBindMountSandboxProvider` or `createIsolatedSandboxProvider`.

**Source:** [https://github.com/mattpocock/sandcastle](https://github.com/mattpocock/sandcastle)
