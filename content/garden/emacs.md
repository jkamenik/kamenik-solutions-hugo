---
title: Emacs
date: '2026-07-23'
lastmod: '2026-07-23'
draft: false
keywords:
- Emacs
- GNU Emacs
params:
  aliases:
  - GNU Emacs
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - ide
---

[Emacs](https://www.gnu.org/software/emacs/) is the GNU project's [[LISP|Lisp]]-powered text editor and long-lived computing environment. We **assess** it as a return candidate now that agent-led terminal work makes the editor interface less central.

## Blurb

> An extensible, customizable, free/libre text editor - and more.

## Summary

Use Emacs when you want one extensible environment for editing, mail, org workflows, and tooling via Emacs Lisp. It may also fit agent-led workflows where most changes happen through a terminal rather than direct editor interaction.

This estate used Emacs as its primary editor for years before moving through [[Atom]], [[VSCode|Visual Studio Code]], and [[Cursor]]. That history lowers relearning risk, but a return should prove practical value beyond nostalgia and existing configuration investment.

Key trade-offs are unmatched customizability and longevity vs a steep learning curve and weaker default agent UX than [[Cursor]]. Compare with [[Vim]] for modal editing without the full Emacs Lisp environment.

## Details

- **Upstream:** https://www.gnu.org/software/emacs/
- **Core model:** Emacs Lisp interpreter plus buffers, modes, and packages
- **Existing configuration:** https://github.com/jkamenik/emacs-prelude-personal
- **Estate history:** Long-term former daily driver, followed by [[Atom]], [[VSCode|Visual Studio Code]], and [[Cursor]]
- **Revisit trigger:** Agent-led terminal editing reduces dependence on a GUI-first editor workflow
- **Fit:** [[Tool]] / [[IDE]] (editor platform, not a headless agent)
- **Contrast:** [[Cursor]] for AI-first daily driving; [[Vim]] for ubiquitous modal editing on servers and remotes
