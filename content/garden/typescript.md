---
title: TypeScript
date: '2026-05-28'
lastmod: '2026-07-02'
draft: false
keywords:
- TypeScript
params:
  garden:
    kind: item
    usefulness: assess
    category: code
    movement: No Change
    subcategories:
    - language
aliases:
- /radar/languages/typescript
---

[TypeScript](https://www.typescriptlang.org/). Is a typed superset of **[[JavaScript]]** that compiles to plain JS.

## Blurb

> TypeScript extends JavaScript by adding types to the language. TypeScript speeds up your development experience by catching errors and providing fixes before you even run your code.

## Summary

**What it is:** Microsoft-maintained language that extends **[[JavaScript]]** with types, interfaces, enums, and generics. The `tsc` compiler (or **[[Bun]]** / esbuild / swc in transpile-only mode) emits JavaScript. Strict mode catches null, implicit any, and API drift at build time.

**When to use:** Large frontends or libraries where static types clearly reduce defect rate. Monorepos with many contributors and a disciplined **[[DevSecOps]]** / **[[Shift Left]]** dependency review. Public APIs that ship `.d.ts` contracts to consumers already on the JS stack.

**When to skip:** One-off scripts, CLIs, and glue where build and type overhead exceed benefit. Latency-sensitive services where interpreted JS runtime cost matters. Teams that want a small dependency footprint and cannot absorb registry risk.

**Before you commit:** map transitive **[[npm]]** dependencies, lockfile policy, and audit cadence. TypeScript does not remove supply-chain risk; it often expands it via tooling packages. Benchmark hot paths on **[[Node.js]]** or **[[Bun]]**, not just compile-time ergonomics.

**Output:** always JavaScript. Pick a target (`ES2022`, etc.) and module format (ESM vs CommonJS) to match your **[[Node.js]]** or bundler pipeline.

## Details

| Topic | Notes |
|-------|--------|
| **Config** | `tsconfig.json` controls strictness, paths, and emit |
| **Gradual adoption** | `allowJs` and `checkJs` migrate legacy **[[JavaScript]]** incrementally |
| **Tooling** | VS Code and most editors use the language service for autocomplete and refactors |
| **Runtime** | Types erase at compile time; no TypeScript VM exists |

**Relationship to JS:** valid **[[JavaScript]]** is valid TypeScript (with `any` where types are omitted). New syntax (e.g. `interface`, `type`) does not exist at runtime. Plain **[[JavaScript]]** remains **hold** for new work; TS is not a free upgrade.

**Risks to weigh**

| Risk | Notes |
|------|--------|
| **Package sprawl** | `tsc`, eslint plugins, framework typings, and test stacks balloon `node_modules` |
| **Supply chain** | public registry incidents; pin lockfiles, audit in CI, prefer verified publishers |
| **Runtime speed** | still JS at execution; CPU-bound work loses to **[[GoLang]]** and similar |

**Alternatives:** plain **[[JavaScript]]** with JSDoc for light typing without a compile step. **[[GoLang]]** or **[[Python]]** when the problem does not need a browser or **[[npm]]** ecosystem.

**References**

- [TypeScript handbook](https://www.typescriptlang.org/docs/handbook/intro.html)
- [TypeScript playground](https://www.typescriptlang.org/play/)
- [TypeScript GitHub repository](https://github.com/microsoft/TypeScript)
