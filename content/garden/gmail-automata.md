---
title: Gmail Automata
date: '2026-06-17'
lastmod: '2026-07-01'
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
    movement: New
---

[Gmail Automata](https://github.com/ranmocy/gmail-automata) is a Google Apps Script project that replaces native Gmail filters with spreadsheet-defined rules. Conditions use Lisp-like S-expressions; actions are independent and composable. We **assess** it because the model is powerful but couples you to Gmail labels, timed Apps Script runs, and a forked Google Sheet. It fits **[[Tool]]** when you want versioned, copy-pasteable email routing across personal and work accounts.

## Blurb

> Gmail Automata is to do a better job replacing existing Gmail filters.

## Summary

Incoming mail is archived by default and tagged `0unprocessed`. A background Apps Script job (default every five minutes) loads unprocessed threads, evaluates rules from the `rules` sheet in stage order, applies matching actions, then moves threads to `0processed`. Unmatched threads surface as errors unless you add a catch-all rule at the end.

Rules and config live in a Google Spreadsheet you fork from the upstream template. That makes backup, reorder, grouping, and sharing rules easier than Gmail's filter UI. The TypeScript source in GitHub deploys to Apps Script via CLASP (`yarn deploy`).

Worth trying when native Gmail filters are hard to maintain or you want one ruleset across accounts. Compare [[gog]] for terminal and agent Gmail access; Automata is filter-and-routing logic inside Gmail, not a general API client.

## Details

- **Runtime:** Google Apps Script bound to a spreadsheet; optional CLASP deploy from the GitHub repo (TypeScript, Yarn).
- **Rule model:** `configs` and `rules` sheets; conditions as S-expressions; staged evaluation stops after the first matching stage unless you design otherwise.
- **Gmail setup:** Minimal native filters route mail into `0unprocessed`; urgent bypass uses `+urgent` in the address. Inbox type "Important first" is optional.
- **Limits:** Each run processes up to 50 threads; very old threads may only evaluate the latest message (2x interval default).
- **Failure mode:** Errors label threads `error`, move them to the inbox, and email the script owner.
- **Activity:** Last push April 2024; ~112 GitHub stars; MIT-style open source from ranmocy.
- **Contrast:** Native Gmail filters (UI-only, no version control); [[gog]] (CLI and JSON for search and mutations, not declarative filter sheets).
