---
title: LISP
date: '2026-07-29'
lastmod: '2026-07-29'
draft: false
keywords:
- LISP
- Common Lisp
params:
  aliases:
  - Common Lisp
  garden:
    kind: item
    usefulness: assess
    category: code
    movement: New
---

[LISP](https://common-lisp.net/) is the family of list-processing languages built on S-expressions, macros, and interactive development. We **assess** it as background for Lisp dialects we evaluate (especially **[[Clojure]]**), not as a default platform language.

## Blurb

> Welcome to the amazing world of Common Lisp, the programmable programming language.

## Summary

**What it is:** A language family (Common Lisp, Scheme, Emacs Lisp, **[[Clojure]]**, and others) where code is data and macros extend the language. Common Lisp is the ANSI-standardized multi-paradigm descendant used as the practical reference dialect.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Learning macros and homoiconicity | Concepts transfer to **[[Clojure]]** and other dialects |
| Long-lived interactive systems | REPL-driven evolution; Common Lisp and Clojure excel here |
| Domain-specific languages | Macro systems make embedded DSLs natural |

**When to skip:**

- Default CLIs, ops tooling, and greenfield services (**[[GoLang|Go]]**)
- Teams without Lisp appetite or REPL culture
- Hiring-sensitive product work where Clojure or Common Lisp depth is thin

**Trade-offs:** Deep expressive power and interactive tooling. Ecosystem and hiring are narrower than Go, Python, or Java. Prefer a concrete dialect note (**[[Clojure]]**) when evaluating project use.

## Details

### Dialects Worth Tracking

| Dialect | Notes |
|---------|--------|
| Common Lisp | ANSI standard; SBCL and others; see [common-lisp.net](https://common-lisp.net/) |
| **[[Clojure]]** | Hosted Lisp on the JVM (and other hosts); our primary Lisp dialect under assessment |
| Scheme / Racket | Smaller core; strong teaching and research use |
| Emacs Lisp | Extension language for Emacs; not a general app runtime choice |

### Related Garden Items

- **[[Clojure]]** - practical Lisp dialect we **assess** for services
- **[[Functional Programming]]** - paradigm Lisp dialects often pair with
- **[[GoLang]]** - default systems language; contrast for ops and CLIs

### References

- [common-lisp.net](https://common-lisp.net/)
- [lisp-lang.org](https://lisp-lang.org/)
- [Wikipedia: Lisp (programming language)](https://en.wikipedia.org/wiki/Lisp_(programming_language))
