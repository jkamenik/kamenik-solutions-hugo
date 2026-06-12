---
title: "npm"
date: 2026-05-28
lastmod: 2026-06-12
draft: false

keywords:
  - npm

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "No Change"
aliases:
  - /radar/tools/npm
---

[npm](https://www.npmjs.com/) is the default package manager and public registry for the **[[JavaScript]]** ecosystem. We **adopt** it as a **[[Tool]]** only when the team is already committed to **[[JavaScript]]** or **[[TypeScript]]**. It ships with **[[Node.js]]**. Do not pick the JS stack mainly for npm. The registry is not a reason to accept supply-chain and dependency-tree risk by itself.

## Blurb

> npm is the package manager for the Node JavaScript platform. It puts modules in place so that node can find them, and manages dependency conflicts intelligently.

## Summary

**What it is:** the `npm` CLI plus the npm Registry (maintained by GitHub). `package.json` declares dependencies, scripts, and metadata. `package-lock.json` pins transitive versions for reproducible installs. Scoped packages (`@org/name`) support private and public monorepo layouts.

**When to use (adopt within the stack):** Existing **[[TypeScript]]** or **[[JavaScript]]** repos on **[[Node.js]]**. Publishing reusable modules after dependency review. CI that runs `npm ci` from a committed lockfile with **[[Shift Left]]** audits.

**When to skip:** Greenfield projects that have not yet justified the JS/TS ecosystem. Latency or footprint-sensitive services where even a slim lockfile is too much. Teams on pnpm, Yarn, or **[[Bun]]** install that dropped the npm CLI. Air-gapped flows that require a private registry only.

**Security:** treat the public registry as a supply-chain surface. Run `npm audit`, pin transitive deps, and gate new packages in **[[DevSecOps]]** review. npm solves dependency resolution; it does not remove registry attack risk.

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
