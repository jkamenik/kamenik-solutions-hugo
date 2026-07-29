---
title: Arrow
date: '2026-07-23'
lastmod: '2026-07-23'
draft: false
keywords:
- Arrow
- Apache Arrow
params:
  aliases:
  - Apache Arrow
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: New
---

[Apache Arrow](https://arrow.apache.org/) is a language-independent columnar memory format plus libraries for fast in-memory analytics and zero-copy interchange. We **trial** it as the in-memory companion to **[[Parquet]]** on disk.

## Blurb

> The universal columnar format and multi-language toolbox for fast data interchange and in-memory analytics

## Summary

**What it is:** Columnar layout for flat and nested data, optimized for CPUs/GPUs. Supports zero-copy reads without serialization tax. Libraries exist across languages; many engines use Arrow for IPC and compute kernels.

**When to use:**

| Situation | Notes |
|-----------|--------|
| In-memory analytics | Share batches across processes without copy |
| Polyglot pipelines | **[[Python]]**, **[[Rust]]**, Java, Go exchange the same buffers |
| Engine plumbing | DuckDB, Spark, and others speak Arrow |

**When to skip:**

- Durable lake storage (**[[Parquet]]** files)
- Simple scripts over small **[[CSV]]** dumps
- No multi-language or zero-copy requirement

**Trade-offs:** Excellent interchange and speed; another format layer to learn. On-disk default remains Parquet for most lakes.

## Details

### Format vs Libraries

| Piece | Role |
|-------|------|
| Arrow format | Spec for columnar memory layout |
| Arrow libraries | Language bindings and compute building blocks |
| Ecosystem | Used inside analytic engines and dataframe stacks |

### Related Garden Items

- **[[Parquet]]** - common on-disk columnar format
- **[[DuckDB]]** - reads/writes Arrow-friendly workflows

### References

- [arrow.apache.org](https://arrow.apache.org/)
