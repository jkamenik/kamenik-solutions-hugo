---
title: Emacs Prelude
date: '2026-07-23'
lastmod: '2026-07-23'
draft: false
keywords:
- Emacs Prelude
- Prelude
- bbatsov Prelude
params:
  aliases:
  - Prelude
  - bbatsov Prelude
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - ide
---

[Emacs Prelude](https://github.com/bbatsov/prelude) is Bozhidar Batsov's enhanced [[Emacs]] 29.1+ distribution with sane defaults and modular packages. We **assess** it as the most familiar path back to Emacs.

## Blurb

> Prelude is an enhanced Emacs 29.1+ distribution that should make your experience with Emacs both more pleasant and more powerful.

## Summary

Use Prelude when you want better defaults and opt-in modules without Spacemacs-scale opinionation. Skip it if you need Evil-first ergonomics ([[Spacemacs]]) or a more finished GUI kit ([[Centaur Emacs]]).

This estate used Prelude as the foundation for its Emacs configuration about a decade ago. The existing personal repository provides a concrete migration baseline, but compatibility with Prelude 2.0 and current Emacs needs validation.

Trade-off: easier to understand and extend vs fewer batteries enabled by default. Prelude 2.0 leans on built-in Eglot and [[tree-sitter]] rather than legacy third-party stacks.

## Details

- **Upstream:** https://github.com/bbatsov/prelude
- **Docs:** https://prelude.emacsredux.com
- **Existing configuration:** https://github.com/jkamenik/emacs-prelude-personal
- **Requires:** GNU Emacs 29.1+
- **Migration concern:** Audit decade-old personal modules against Prelude 2.0 before reuse
- **Philosophy:** Simple, stable foundation; modules mostly opt-in; not Evil by default
- **Fit:** [[Tool]] / [[IDE]] as an Emacs distribution
- **Contrast:** [[Spacemacs]] (Evil + layers), [[Centaur Emacs]] (heavier out-of-box UI), [[Cursor]] (non-Emacs AI IDE)
