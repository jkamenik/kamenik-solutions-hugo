---
title: npm
date: '2026-05-28'
lastmod: '2026-07-02'
draft: false
keywords:
- npm
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
aliases:
- /radar/tools/npm
---

[npm](https://www.npmjs.com/). Is the default package manager and public registry for the **[[JavaScript]]** ecosystem.

## Summary

**Garden stance:** We **trial** npm for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

| Command | Role |
|---------|------|
| **`npm install`** | Add or update dependencies; writes lockfile when configured |
| **`npm ci`** | Clean install from lockfile (preferred in CI) |
| **`npm run`** | Execute `scripts` entries in `package.json` |
| **`npm publish`** | Push a package version to a registry |
| **`npm audit`** | Report known vulnerabilities in the dependency tree |

**Ships with Node:** installing **[[Node.js]]** includes npm. Version bumps track Node releases; use `corepack` if you enable pnpm or Yarn officially.

**Registry:** largest public **[[JavaScript]]** package index. Complexity scales with transitive dependencies; monorepos need workspace discipline.

**Rating note:** garden default is **trial** because npm alone is not grounds to enter JS/TS. Once committed to that stack, treat npm as **adopt** for installs and scripts.

**Alternatives:** **[[Bun]]** as an npm-compatible install client. pnpm and Yarn (not in garden) for stricter monorepo layouts and deduplicated stores.

**Not the acronym you think:** npm officially expands to "npm is not an acronym."

**References**

- [About npm](https://docs.npmjs.com/about-npm/)
- [npm CLI documentation](https://docs.npmjs.com/cli/v11/commands/npm)
- [npm Registry](https://www.npmjs.com/)
