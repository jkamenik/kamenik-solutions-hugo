---
title: cljgo
date: '2026-07-24'
lastmod: '2026-07-24'
draft: false
keywords:
- cljgo
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: New
---

[cljgo](https://github.com/muthuishere/cljgo) is a Clojure host on Go: AOT to plain Go source plus a tree-walk REPL. We **assess** it as an experimental path to Clojure semantics with static Go binaries and zero-binding Go interop.

## Blurb

> The same source runs interpreted at the prompt and compiles to a single static native binary, with byte-identical output on both paths.

## Summary

**What it is:** Compiler and REPL written in Go. Same dual-mode idea as ClojureScript, with Go as the emit target. `require-go` calls any Go module without hand-written bindings. `cljgo build` emits a static native binary (no JVM runtime).

**When to use:**

| Situation | Notes |
|-----------|--------|
| Clojure syntax, Go deploy | Want REPL + single static binary |
| Go ecosystem as stdlib | Call Go packages live from Clojure |
| Cross-compile from one host | `cljgo dist` targets many GOOS/GOARCH pairs |
| Tiny container images | AOT web template (`bri`) claims scratch-friendly binaries |

**When to skip:**

- Production-critical services (project is early; assess only)
- Teams standardized on JVM Clojure tooling and libraries
- Simple Go programs where Lisp is not the goal (**[[GoLang|Go]]** alone)

**Trade-offs:** Strong story for interop and dual-mode fidelity. Young project; ecosystem and long-term stewardship are unproven versus JVM Clojure.

## Details

### Modes

| Command | Role |
|---------|------|
| `cljgo repl` / `nrepl` | Interpreted REPL; Calva/CIDER connect |
| `cljgo run` | Interpret a file |
| `cljgo build` | AOT to a static Go binary (needs Go toolchain) |
| `cljgo new` | Project templates: lib, cli, web |
| `cljgo dist` | Cross-compile release artifacts |

### Related Garden Items

- **[[Clojure]]** - the language semantics cljgo aims to host
- **[[GoLang]]** - emit target and interop surface
- **[[Bun]]** - peer pattern: language stays separate; this is the runtime/toolchain
- **[[Functional Programming]]** - paradigm fit for Clojure-on-Go experiments

### References

- [GitHub: muthuishere/cljgo](https://github.com/muthuishere/cljgo)
- [Docs site](https://muthuishere.github.io/cljgo/)
- [pkg.go.dev](https://pkg.go.dev/github.com/muthuishere/cljgo)
