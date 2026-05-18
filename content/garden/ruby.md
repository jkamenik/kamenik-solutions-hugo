---
title: "Ruby"
date: 2025-12-08
lastmod: 2026-05-17
draft: false

keywords:
  - Ruby

params:
  garden:
    kind: item
    usefulness: hold
    category: code
    movement: "No Change"
    subcategories:
      - language

aliases:
  - /radar/languages/ruby
---

[Ruby](https://www.ruby-lang.org/en/) is a dynamic, expressive language optimized for developer ergonomics and metaprogramming. We rate it **hold** for new work: it remains viable for maintaining existing codebases (especially [[Ruby on Rails]]), but hiring depth, runtime performance, and ecosystem momentum outside that niche favor other stacks for greenfield systems.

## Blurb

> Ruby is a language of careful balance. Its creator, Yukihiro "Matz" Matsumoto, blended parts of his favorite languages (Perl, Smalltalk, Eiffel, Ada, and Lisp) to form a new language that balanced functional programming with imperative programming.

## Summary

In the 2000s Ruby stood out for treating the programmer as the customer—readable syntax, blocks, and open classes made it feel like a DSL you could shape in place. That flexibility powered the Rails era but also encouraged "magic" (monkey patches, implicit requires, metaprogramming) that is hard to audit in large teams.

Outside the Rails corridor, Ruby sees less investment in performance (GIL, interpreter overhead) and tooling compared to [[GoLang]] for infra or [[Python]] for data/ML. Keep Ruby when you inherit a mature app or a team that already ships it; do not default to it for new platforms.

## Details

- **Sweet spot:** long-lived web monoliths on [[Ruby on Rails]]; scripting and glue where team expertise already exists.
- **Friction:** slow cold starts and CPU-bound workloads vs compiled or JIT languages; global interpreter lock limits naive threading models.
- **Ecosystem:** gems are plentiful but quality varies; operations patterns often trace to [[Capistrano]]-era deploys rather than modern container-native defaults.
- **Pair with:** [[Ruby on Rails]] (framework, also **hold** for greenfield); prefer [[Python]] or [[GoLang]] when starting net-new services without a Ruby mandate.
