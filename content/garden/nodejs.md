---
title: Node.js
date: '2026-05-28'
lastmod: '2026-07-02'
draft: false
keywords:
- Node.js
params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: No Change
aliases:
- /radar/tools/nodejs
---

[Node.js](https://nodejs.org/). Is a cross-platform runtime that executes [[JavaScript]] outside the browser, built on V8.

## Blurb

> Node.js® is a free, open-source, cross-platform JavaScript runtime environment that lets developers create servers, web apps, command line tools and scripts.

## Summary

**Garden stance:** We **adopt** Node.js for our estate.

**Key points:** | Topic | Notes |
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
