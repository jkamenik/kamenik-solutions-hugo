---
title: Clojure
date: '2026-07-24'
lastmod: '2026-07-29'
draft: false
keywords:
- Clojure
params:
  garden:
    kind: item
    usefulness: assess
    category: code
    movement: No Change
---

[Clojure](https://clojure.org/) is a **[[LISP|Lisp]]** dialect with persistent data structures, macros, and a strong functional core. We **assess** it for REPL-driven services and FP-heavy domains where JVM hosting is acceptable.

## Blurb

> Clojure is a robust, practical, and fast programming language with a set of useful features that together form a simple, coherent, and powerful tool.

## Summary

**What it is:** Hosted Lisp on the JVM (and dialects on other hosts). Immutable defaults, software transactional memory for shared state, and first-class interop with Java libraries. Sibling of the broader **[[LISP]]** family.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Interactive systems work | Grow the program live with a REPL |
| Concurrent shared state | Prefer STM and agents over ad-hoc locks |
| Java ecosystem access | Call JVM libraries without leaving the language |
| FP-first teams | Pairs with **[[Functional Programming]]** practice |

**When to skip:**

- Default platform CLIs and ops tooling (**[[GoLang|Go]]**)
- Teams without Lisp or JVM appetite
- Ultra-small cold-start binaries without Graal or an alternate host like **[[cljgo]]**

**Trade-offs:** Excellent data and concurrency model; JVM startup and ops cost remain the usual friction. Hiring and onboarding are narrower than Go or Python.

## Details

### Hosts and Dialects

| Host | Notes |
|------|--------|
| JVM Clojure | Canonical implementation; Java interop |
| ClojureScript | Same ideas targeting **[[JavaScript]]** |
| **[[cljgo]]** | Experimental Clojure hosted on **[[GoLang|Go]]** (AOT to Go source) |

### Related Garden Items

- **[[LISP]]** - language family; Clojure is the dialect we evaluate for services
- **[[Functional Programming]]** - paradigm we **adopt**; Clojure is a practical FP language
- **[[cljgo]]** - alternate host aimed at static Go binaries and Go ecosystem interop
- **[[GoLang]]** - our default systems language; contrast for ops and CLIs

### References

- [clojure.org](https://clojure.org/)
- [GitHub: clojure/clojure](https://github.com/clojure/clojure)
