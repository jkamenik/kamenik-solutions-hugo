---
title: "Bun"
date: 2026-05-28
lastmod: 2026-06-22
draft: false

keywords:
  - Bun

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "No Change"
aliases:
  - /radar/tools/bun
---

[Bun](https://bun.sh/) is an all-in-one JavaScript runtime, package manager, test runner, and bundler in a single binary. We rate it **trial** as a **[[Tool]]** that runs JavaScript and TypeScript. It targets **[[Node.js]]** API compatibility with faster startup. Adopt incrementally (`bun install`, `bun test`) before swapping the production runtime.

## Blurb

> Bun is a fast, incrementally adoptable all-in-one JavaScript, TypeScript and JSX toolkit. Use individual tools like bun test or bun install in Node.js projects, or adopt the complete stack with a fast JavaScript runtime, bundler, test runner, and package manager built in.

## Summary

**What it is:** Bun ships one executable built with Zig on JavaScriptCore. It implements many Node and Web APIs natively. TypeScript and JSX run without extra config. Built-in SQLite, Redis, and PostgreSQL clients reduce dependency sprawl for common backends.

**When to use:**

- New services where cold start and install speed matter
- Scripts and CLIs that benefit from fast launch
- Teams tired of juggling separate bundler, test, and package-manager tools
- Drop-in trials on existing **[[Node.js]]** repos via `bun install` or `bun test`

**When to skip:** Production stacks that depend on niche native addons untested on Bun. Org policy that mandates Node LTS only. Workloads where **[[Node.js]]** maturity and OpenJS governance outweigh raw speed.

**Incremental path:** Keep Node in CI while developers use Bun locally. Validate native modules and edge-case APIs before cutting over the runtime in production.


## Details

| Tool | Role |
|------|------|
| **`bun run`** | Execute scripts and TypeScript entrypoints |
| **`bun install`** | npm-compatible lockfile and registry client |
| **`bun test`** | Jest-compatible test runner with fast startup |
| **`bun build`** | Bundle JS, TS, and JSX for server or browser targets |
| **`Bun.serve`** | HTTP server with WebSocket support |

**Compatibility:** Bun aims for broad Node API parity but gaps remain in native addons and obscure modules. Run your test suite and integration checks before declaring parity.

**Process management:** **[[PM2]]** supports Bun since v1. Same cluster and reload patterns apply as for Node.

**Engine difference:** JavaScriptCore (Safari) vs V8 (Node). Performance profiles differ; benchmark your app rather than assuming universal wins.

**Alternatives:** **[[Node.js]]** remains the conservative default JavaScript runtime on the server.

**References**

- [Bun documentation](https://bun.com/docs)
- [Bun GitHub repository](https://github.com/oven-sh/bun)
- [Node.js compatibility](https://bun.com/docs/runtime/nodejs-apis)
