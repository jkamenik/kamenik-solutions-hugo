---
title: WASM
date: '2026-07-23'
lastmod: '2026-07-29'
draft: false
keywords:
- WASM
- WebAssembly
params:
  aliases:
  - WebAssembly
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
---

[WebAssembly](https://webassembly.org/) (Wasm) is a portable binary instruction format for a stack-based VM. We **trial** it as a compile target for near-native code in browsers, edge, and embeddable runtimes.

## Blurb

> WebAssembly (abbreviated Wasm) is a binary instruction format for a stack-based virtual machine. Wasm is designed as a portable compilation target for programming languages, enabling deployment on the web for client and server applications.

## Summary

**What it is:** Open W3C standard. Size- and load-efficient binary format aiming for near-native speed. Sandboxed; works with **[[JavaScript]]** on the web and in non-web embeddings (**[[Node.js]]**, edge workers, databases).

**When to use:**

| Situation | Notes |
|-----------|--------|
| Heavy browser compute | Port **[[Rust]]**/C++/Go hot paths into the page |
| Portable plugins | Ship one binary across hosts that embed Wasm |
| Edge / serverless | Small cold start vs full containers in some platforms |
| Embedded analytics | Engines like **[[DuckDB]]** ship Wasm clients |

**When to skip:**

- Simple UI and I/O-bound Node services (plain JS/TS is enough)
- Need for full OS syscalls without WASI or host glue
- Teams without a language that compiles cleanly to Wasm

**Trade-offs:** Great portability and sandboxing; debugging and host ABI complexity remain. Not a replacement for native services when you control the OS.

## Details

### Ecosystem Notes

| Topic | Notes |
|-------|--------|
| Standards | W3C Community Group and Working Group |
| Text format | Human-readable for debug and teaching |
| Hosts | Browsers, Node, Wasmer/Wasmtime, many embedders |
| Languages | **[[Rust]]**, C/C++, Go, and others compile to Wasm |

### References

- [webassembly.org](https://webassembly.org/)
- [MDN WebAssembly](https://developer.mozilla.org/en-US/docs/WebAssembly)
