---
title: JavaScript
date: '2026-05-28'
lastmod: '2026-07-02'
draft: false
keywords:
- JavaScript
params:
  garden:
    kind: item
    usefulness: hold
    category: code
    movement: No Change
    subcategories:
    - language
aliases:
- /radar/languages/javascript
---

[JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript). We **hold** it under **[[Code]]** in the garden.

## Summary

**What it is:** ECMAScript defines the language; "JavaScript" is the practical name in browsers and on the server. It is dynamic, prototype-based, and garbage-collected. TC39 ships yearly language updates. Host environments add APIs (DOM in browsers, `fs` and HTTP in **[[Node.js]]**).

**When to use:** Maintaining existing plain-JS codebases. Tiny browser snippets where a **[[TypeScript]]** build step adds no value. Learning ECMAScript fundamentals before layering types.

**When to skip:** New application code where **[[TypeScript]]** is viable. Large teams without static types. Backend services where **[[GoLang]]** or another language fits better than the JS toolchain.

**Not the same as:** **[[Node.js]]** or **[[Bun]]** (runtimes), **[[npm]]** (package manager), or **[[JSON]]** (data format).

## Details

| Topic | Notes |
|-------|--------|
| **Standard** | ECMA-262 (ECMAScript); proposals public on [tc39](https://github.com/tc39) |
| **Modules** | ESM (`import`/`export`) is the modern default; CommonJS persists in older Node code |
| **Typing** | Plain JS is dynamically typed; prefer **[[TypeScript]]** (**assess**) for new typed work |
| **Runtimes** | **[[Node.js]]** (**adopt**) for server and tooling; **[[Bun]]** (**trial**) as a faster alternative engine |

**Default for new code:** **[[TypeScript]]** over plain JS when the team accepts the JS ecosystem tradeoffs (see that note for supply-chain and runtime cost).

**Ecosystem:** **[[npm]]** registry holds millions of packages. Most frontend and test tooling (**[[Playwright]]**, bundlers, frameworks) assumes **[[TypeScript]]** or JavaScript source.

**Alternatives:** **[[TypeScript]]** for greenfield work in the same runtime family. **[[GoLang]]** or **[[Python]]** when leaving the browser/Node toolchain entirely.

**References**

- [JavaScript on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [ECMAScript language specification](https://tc39.es/ecma262/)
- [JavaScript technologies overview](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/JavaScript_technologies_overview)
