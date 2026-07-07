---
title: Bun
date: '2026-05-28'
lastmod: '2026-07-02'
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

[Bun](https://bun.sh/). Is an all-in-one JavaScript runtime, package manager, test runner, and bundler in a single binary.

## Summary

**Garden stance:** We **trial** Bun for our estate.

**Key points:** | Tool | Role |
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
