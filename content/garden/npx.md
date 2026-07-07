---
title: npx
date: '2026-05-28'
lastmod: '2026-07-02'
draft: false
keywords:
- npx
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
aliases:
- /radar/tools/npx
---

[npx](https://docs.npmjs.com/cli/v11/commands/npx). Runs executables from **[[npm]]** packages without a global install.

## Blurb

> Run a command from a local or remote npm package

## Summary

**Garden stance:** We **trial** npx for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

| Pattern | Role |
|---------|------|
| **`npx webpack`** | Run a locally installed binary from `node_modules/.bin` |
| **`npx --package=foo@1.2.3 -- foo`** | Pin version when binary name differs from package name |
| **`npx -c 'eslint .'`** | Run a shell string with package binaries on `PATH` |
| **`npm exec -- ...`** | Same capability; use `--` to pass flags to the child command |

**vs [[npm]]:** **[[npm]]** installs and declares dependencies. npx executes them. Most projects should declare tools in `devDependencies` and call them via `npm run`, not one-off remote `npx` in CI.

**Rating note:** garden default is **trial** for the same reason as **[[npm]]**. Once on JS/TS, adopt npx for local binary execution; avoid casual remote runs without **[[Shift Left]]** review.

**Alternatives:** **[[npm]]** `exec` and `run` scripts. **[[Bun]]** `bunx` for Bun-first repos. Global installs (discouraged for rarely used tools).

**References**

- [npx command](https://docs.npmjs.com/cli/v11/commands/npx)
- [npm exec](https://docs.npmjs.com/cli/v11/commands/npm-exec)
- [About npm](https://docs.npmjs.com/about-npm/)
