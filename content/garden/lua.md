---
title: Lua
date: '2026-08-24'
lastmod: '2026-08-24'
draft: false
keywords:
- Lua
params:
  garden:
    kind: item
    usefulness: trial
    category: language
    movement: No Change
---

[Lua](https://www.lua.org/) is a lightweight, high-level, embeddable scripting language designed for extending applications. We trial it for agent-scriptable tools like SilverBullet's Space Lua.

## Blurb

> Lua is a powerful, efficient, lightweight, embeddable scripting language. It supports procedural programming, object-oriented programming, functional programming, data-driven programming, and data description.

## Summary

**When to use:** Choose Lua for embedding scripting in applications, configuration, or when you need a small, fast, easily embeddable language with minimal runtime.

**When to skip:** Opt for Python or JavaScript when you need large ecosystems, heavy libraries, or general-purpose application development.

**Key trade-offs:**
- **Pros:** Tiny footprint (~200KB), fast execution, simple C API, portable, coroutines, tables as only data structure
- **Cons:** Minimal standard library, smaller ecosystem, 1-based indexing, no built-in classes/modules

**Related:** [[SilverBullet]] [[Markdown]] [[PKM]] [[Agent Skills Framework]]

## Details

| Topic | Notes |
|-------|--------|
| **Runtime** | ~200KB, ANSI C, runs everywhere |
| **Embedding** | Designed for C/C++ host applications |
| **Data Model** | Tables (associative arrays) as sole composite structure |
| **Concurrency** | Cooperative coroutines (not threads) |
| **Variants** | LuaJIT (fast JIT), MoonSharp (.NET), GopherLua (Go) |
| **Notable Uses** | Redis, Nginx (OpenResty), Wireshark, SilverBullet Space Lua |
