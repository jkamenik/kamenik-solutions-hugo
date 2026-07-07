---
title: Gmail Automata
date: '2026-06-17'
lastmod: '2026-07-02'
draft: false
keywords:
- Gmail Automata
- gmail-automata
params:
  aliases:
  - gmail-automata
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
---

[Gmail Automata](https://github.com/ranmocy/gmail-automata). Is a Google Apps Script project that replaces native Gmail filters with spreadsheet-defined rules.

## Blurb

> Automate your Gmail. Contribute to ranmocy/gmail-automata development by creating an account on GitHub.

## Summary

**Garden stance:** We **assess** Gmail Automata for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

- **Runtime:** Google Apps Script bound to a spreadsheet; optional CLASP deploy from the GitHub repo (TypeScript, Yarn).
- **Rule model:** `configs` and `rules` sheets; conditions as S-expressions; staged evaluation stops after the first matching stage unless you design otherwise.
- **Gmail setup:** Minimal native filters route mail into `0unprocessed`; urgent bypass uses `+urgent` in the address. Inbox type "Important first" is optional.
- **Limits:** Each run processes up to 50 threads; very old threads may only evaluate the latest message (2x interval default).
- **Failure mode:** Errors label threads `error`, move them to the inbox, and email the script owner.
- **Activity:** Last push April 2024; ~112 GitHub stars; MIT-style open source from ranmocy.
- **Contrast:** Native Gmail filters (UI-only, no version control); [[gog]] (CLI and JSON for search and mutations, not declarative filter sheets).
