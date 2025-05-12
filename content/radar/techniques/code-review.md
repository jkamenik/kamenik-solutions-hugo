---
title: 'Code Review'
date: 2025-04-09
lastmod: 2025-05-11

aliases:
  - radar/techniques/merge-request
  - radar/techniques/pull-request

# Keywords help in classifying content
keywords:
  - Merge Request
  - Pull Request
  - Code Review

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: adopt

    # tools, techniques, platforms, languages & frameworks
    quadrant: techniques

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

A code review should involve both human (if possible) and machine review.  Any opposition, such as unresolved comments, failed automated checks, or policy violations, should block the review from being merged.  Luckily most Source Version Control (SVC) systems like {{% wl "GitHub" %}}, {{% wl "GitLab" %}}, and {{% wl "Gerrit" %}} have a code review process that is built into their merge process.  It should be the entry point to the {{% wl "Continuous Integration" %}} process, and should be adopted by all teams.

Even if you are a party of 1, having machine review centralized in a standard code review process will save you a lot of headaches.

<!--more-->

## Nominclature

GitHub calls it a Pull Request, sometimes appreviated PR.

GitLab calls it a Merge Request, sometimes appreviated MR.
