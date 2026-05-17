---
title: "Code Review"
date: 2025-04-09
lastmod: 2026-05-17
draft: false

keywords:
  - Code Review

params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "No Change"

aliases:
  - /radar/techniques/code-review
---

[Code Review](https://en.wikipedia.org/wiki/Code_review)

A code review should involve both human (if possible) and machine review. Any opposition, such as unresolved comments, failed automated checks, or policy violations, should block the review from being merged. Luckily most Source Version Control (SVC) systems like [[GitHub]], [[GitLab]], and [[Gerrit]] have a code review process that is built into their merge process. It should be the entry point to the [[Continuous Integration]] process, and should be adopted by all teams.

Even if you are a party of 1, having machine review centralized in a standard code review process will save you a lot of headaches.

## Nominclature

GitHub calls it a Pull Request, sometimes abbreviated PR.

GitLab calls it a Merge Request, sometimes abbreviated MR.
