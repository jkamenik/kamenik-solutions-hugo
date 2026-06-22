---
title: "Node.js"
date: 2026-05-28
lastmod: 2026-06-22
draft: false

keywords:
  - Node.js

params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: "No Change"
aliases:
  - /radar/tools/nodejs
---

[Node.js](https://nodejs.org/) is a cross-platform runtime that executes [[JavaScript]] outside the browser, built on V8. We **adopt** it as a **[[Tool]]**, for when you MUST use [[JavaScript]] / [[TypeScript]]; Node is the default engine for server-side JS, CLIs, and [[npm]]-based tooling unless you standardize on **[[Bun]]**.

## Blurb

> Node.js is a free, open-source, cross-platform JavaScript runtime environment that lets developers create servers, web apps, command line tools and scripts.

## Summary

**What it is:** Node.js runs JavaScript outside the browser with non-blocking I/O via libuv. The standard library covers HTTP, streams, crypto, filesystem access, and worker threads. npm is the default package registry; most JavaScript tooling assumes Node-compatible APIs.

**When to use:** APIs and microservices with heavy network or DB I/O. Real-time apps (WebSockets, SSE). Full-stack teams that share JavaScript between browser and server. Tooling that must run wherever CI and laptops already ship Node.

**When to skip:** CPU-bound numeric work on a single thread without worker offload. Stacks that forbid JavaScript on the server entirely. Workloads better served by a compiled runtime when npm breadth is not the deciding factor.

**Runtime model:** JavaScript runs on one main thread per process. Async work delegates to the thread pool and OS. Scale out with cluster mode, **[[PM2]]**, or containers rather than expecting threads inside one process.


## Details

| Topic | Notes |
|-------|--------|
| **LTS releases** | Even-numbered majors get long-term support; pin versions in production |
| **Modules** | ESM (`import`) is default in new projects; CommonJS (`require`) still common in older code |
| **Package manager** | npm ships with Node; pnpm and yarn remain popular for monorepos |
| **Testing** | Jest, Vitest, and node:test cover unit and integration layers |
| **Observability** | **[[OpenTelemetry]]** and structured logging integrate well with **[[REST]]** services |

**Ecosystem:** largest registry for web and automation libraries. **[[Playwright]]**, bundlers, and frontend tooling all target Node first.

**Process management:** **[[PM2]]** daemonizes Node apps on bare metal. Prefer **[[Docker]]** when you need reproducible images and orchestration.

**Alternatives:** **[[Bun]]** as a faster drop-in JavaScript runtime for many workloads.

**References**

- [Node.js documentation](https://nodejs.org/docs/latest/api/)
- [About Node.js](https://nodejs.org/en/about)
- [Node.js GitHub repository](https://github.com/nodejs/node)
