---
title: Rust
date: '2026-07-23'
lastmod: '2026-07-23'
draft: false
keywords:
- Rust
params:
  garden:
    kind: item
    usefulness: trial
    category: code
    movement: New
    subcategories:
    - language
---

[Rust](https://www.rust-lang.org/) is a systems language with ownership-based memory safety and no garbage collector. We **trial** it for performance-critical services, CLIs, and WASM modules where **[[GoLang|Go]]** or **[[Python]]** are not enough.

## Blurb

> Empowering everyone to build reliable and efficient software.

## Summary

**What it is:** Compiled language with a strong type system, fearless concurrency story, and Cargo tooling (build, test, publish). Used for network services, embedded, CLI tools, and **[[WASM]]** targets.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Memory-safe systems code | Replace C/C++ hotspots without GC pauses |
| High-performance services | Predictable latency and small footprint |
| WASM modules | Compile to **[[WASM]]** for browser or edge |
| Shared library boundaries | FFI into Python/Node where safety matters |

**When to skip:**

- Fast CRUD apps and scripts (**[[Python]]**, **[[Node.js]]**)
- Teams without Rust ramp budget (ownership learning curve)
- Greenfield platform tooling where **[[GoLang|Go]]** already fits

**Trade-offs:** Excellent safety and speed; slower to write and hire for than Go or Python. Compile times and borrow-checker friction are real.

## Details

### Tooling

| Tool | Role |
|------|------|
| rustup | Toolchain install and channel management |
| Cargo | Build, test, doc, publish to crates.io |
| rustfmt / Clippy | Format and lint |
| rust-analyzer | Editor LSP |

### Related Garden Items

- **[[GoLang]]** - default systems/DevOps language we **adopt**
- **[[WASM]]** - common compile target for Rust on the web
- **[[DuckDB]]** - ships a Rust client among others

### References

- [rust-lang.org](https://www.rust-lang.org/)
- [GitHub: rust-lang/rust](https://github.com/rust-lang/rust)
