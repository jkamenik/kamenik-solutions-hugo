---
title: "Design Pattern"
date: 2026-04-16
lastmod: 2026-06-12
draft: false

keywords:
  - Design Pattern
  - Design Patterns

params:
  aliases:
    - Design Patterns
  garden:
    kind: subcategory
    parent_category: technique
    subcategory_slug: design-pattern
---

Under **[[Technique]]**, **Design Pattern** groups **named, reusable solutions** to recurring problems in code structure and collaboration (usually at class/module granularity). Patterns are vocabulary for review and design, not a checklist to apply everywhere.

**In this subcategory:** classic OOP patterns (GoF-style), idiomatic patterns per language (for example concurrency patterns in Go), and small-scale structural choices (repository, strategy, adapter) documented as **items** when they deserve a garden page.

**Not here:** cloud **architecture** patterns (put under **[[Platform]]** / **[[Declarative IaC]]** notes), **[[Framework]]** conventions (Rails, Spring), **[[Specification]]** standards (OpenAPI, ZTNA specs), or **[[AI Techniques]]** (prompt/skill patterns).

**Sibling subcategory:** **[[Specification]]** for externally defined standards; both sit under **[[Technique]]** alongside practices like **[[Code Review]]** and **[[Continuous Integration]]**.

**Garden stance:**

- **Adopt** patterns when they **name real pain** (duplication, tangled dependencies, unclear extension points) and the team will maintain the abstraction.
- **Hold** pattern-first design, deep inheritance trees, and "enterprise" layers that exist only because a book said so.
- Prefer **simple functions + data** until a pattern pays rent; in Go and similar languages, favor **composition** over ceremony (see [Go Concurrency Patterns](resources/blog/20141017-go-concurrency-patterns.md) for idiomatic concurrency patterns).

**How to tag an item:** create a garden **item** (no `Type`) under **[[Technique]]** with `subcategories: ["[[Design Pattern]]"]` when documenting one pattern's forces, trade-offs, and when *not* to use it.

**Common families (for future items):**

| Family | Examples |
|--------|----------|
| Creational | Factory, Builder, Singleton (use sparingly) |
| Structural | Adapter, Facade, Decorator |
| Behavioral | Strategy, Observer, Command, Template Method |

**References**

- [Wikipedia: Software design pattern](https://en.wikipedia.org/wiki/Software_design_pattern)
