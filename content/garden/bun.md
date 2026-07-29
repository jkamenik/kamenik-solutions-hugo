---
title: Bun
date: '2026-05-28'
lastmod: '2026-07-29'
draft: false
keywords:
- Bun
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
aliases:
- /radar/tools/bun
---

[Bun](https://bun.sh/) is an all-in-one JavaScript and TypeScript toolkit: runtime, package manager, test runner, and bundler in one binary. We **trial** it where startup time and toolchain simplicity matter more than full **[[Node.js]]** ecosystem certainty.

## Blurb

> Bun is a fast, incrementally adoptable all-in-one JavaScript, TypeScript & JSX toolkit.

## Summary

**What it is:** One binary replacing several tools. Built on JavaScriptCore instead of V8. Adoptable piecemeal: use `bun install` or `bun test` inside an existing **[[Node.js]]** project without switching runtimes.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Slow npm installs | `bun install` as a drop-in, much faster client |
| Jest suites that drag | `bun test` keeps the `expect()` API |
| CLIs and scripts | Fast start; single-file executables |
| Zero-config TypeScript | Runs `.ts` and `.tsx` without a build step |

**When to skip:**

- Production services that depend on native addons or obscure Node modules
- Teams that need the conservative default runtime (**[[Node.js]]**)
- Anything where an unproven engine profile is an unacceptable risk

**Trade-offs:** Real speed wins on install, test, and cold start. Node compatibility is a goal, not a guarantee. Adopt one tool at a time and verify with your own suite before moving a whole service.

## Details

| Tool | Role |
|------|------|
| **`bun run`** | Execute scripts and TypeScript entrypoints |
| **`bun install`** | npm-compatible lockfile and registry client |
| **`bun test`** | Jest-compatible test runner with fast startup |
| **`bun build`** | Bundle JS, TS, and JSX for server or browser targets |
| **`Bun.serve`** | HTTP server with routing and WebSocket support |

**Compatibility:** Bun targets broad Node API parity, but gaps remain in native addons and less common modules. Run your test suite and integration checks before declaring parity.

**Process management:** **[[PM2]]** supports Bun since v1. The same cluster and reload patterns apply as for Node.

**Engine difference:** JavaScriptCore (Safari) versus V8 (Node). Performance profiles differ. Benchmark your own app rather than assuming universal wins.

**Batteries included:** Built-in SQL clients, S3 and Redis helpers, shell scripting via `Bun.$`, and YAML imports. Convenient, but each one is a coupling to Bun-specific APIs.

**References**

- [Bun documentation](https://bun.com/docs)
- [Bun GitHub repository](https://github.com/oven-sh/bun)
- [Node.js compatibility](https://bun.com/docs/runtime/nodejs-apis)
