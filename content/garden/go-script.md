---
title: "go script"
date: 2026-05-27
lastmod: 2026-05-27
draft: false

keywords:
  - go script

params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "New"

aliases:
  - /radar/techniques/go-script
---

[go script](https://www.thoughtworks.com/insights/blog/praise-go-script-part-i)

The **go script** pattern (often `./go` at repo root) is a small **[[GoLang]]** program that replaces Make for project tasks: build, test, lint, and release with one cross-platform entrypoint. We **adopt** it for repos where Make is painful on Windows and shell scripts sprawl across OSes.

## Blurb

> A single Go file at the root of your repository can act as a portable task runner with typed logic, subcommands, and access to the full Go standard library.

## Summary

**How it works:** developers run `./go test` or `go run ./go test` (depending on shebang and execute bits). Subcommands map to functions; flags use `flag` or cobra if the script grows.

**When to use:** polyglot teams need identical commands on macOS, Linux, and Windows; tasks need real code (API calls, code gen) not just shell pipelines.

**When to skip:** the repo is already standardized on **[[Dagu]]**, Nx, or a monorepo tool; a thin Makefile plus documented scripts is enough.

**Reference:** ThoughtWorks write-up linked in `url`; pair with **[[git]]** hooks or **[[GitHub Actions]]** calling the same `./go` targets in CI.
