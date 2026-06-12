---
title: "npx"
date: 2026-05-28
lastmod: 2026-06-12
draft: false

keywords:
  - npx

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
aliases:
  - /radar/tools/npx
---

[npx](https://docs.npmjs.com/cli/v11/commands/npx) runs executables from **[[npm]]** packages without a global install. It ships with **[[Node.js]]** (via npm 5.2+). We **adopt** it as a **[[Tool]]** only when the team is already on **[[JavaScript]]** or **[[TypeScript]]**. Ad-hoc `npx` against the public registry is a supply-chain risk; pin versions and prefer lockfile-local binaries in CI.

## Blurb

> Run a command from a local or remote npm package.

## Summary

**What it is:** a runner for package binaries. It resolves commands from `./node_modules/.bin`, or downloads a package temporarily when the binary is missing. Modern npm implements `npx` as a wrapper around `npm exec`. Common for one-off scaffolds (`npx create-*`) and running local dev tools without typing full paths.

**When to use (adopt within the stack):** Run project-local CLIs (`npx vitest`, `npx eslint`) in docs and scripts. Try a generator once with an explicit `@version` pin. CI that executes only lockfile-installed binaries (after `npm ci`).

**When to skip:** Running unpinned remote packages in production or privileged environments. Teams not yet committed to the JS/TS stack. Flows where **[[Bun]]** `bunx` or committed `package.json` scripts are enough.

**Security:** `npx some-tool` can pull and execute code from the registry on demand. Treat that like running untrusted software. Prefer `npm exec --package=foo@1.2.3 -- foo` with a pinned version, or depend on the package in `package.json` and use `npm run`.

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
