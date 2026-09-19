---
title: iTerm2
date: '2026-09-18'
lastmod: '2026-09-18'
draft: false
keywords:
- iTerm2
params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: New
---

[iTerm2](https://iterm2.com) is the long-time macOS terminal replacement and the resolved Mac client for the TUI IDE stack. We **adopt** it because it is the only candidate whose custom URL schemes stay clickable.

## Blurb

> iTerm2 is a replacement for Terminal and the successor to iTerm. It works on Macs with macOS 10.14 or newer. iTerm2 brings the terminal into the modern age with features you never knew you always wanted.

## Summary

Use iTerm2 on macOS as the primary terminal. It won the Mac terminal decision over [[Ghostty]] and [[Supacode]] because Ghostty recognizes only a hard-coded list of clickable URL schemes, and the fix for custom schemes was closed as not planned upstream.

Configure it manually: custom prefs folder, Nerd Font, warm-burnout theme, Shift+Enter binding. It pairs with [[herdr]] and [[Mosh]] for the remote VPS half of the stack.

Its roughly 12 ms input latency versus Ghostty's 2 ms is invisible when waiting for an Agent or at VPS round-trip distances.

## Details

- **Upstream:** https://iterm2.com
- **Role:** Mac terminal client in the TUI IDE stack
- **Deciding factor:** handles `obsidian://` and `onepassword://` links; Ghostty does not
- **Input latency:** about 12 ms vs Ghostty 2 ms, invisible at VPS round-trip distances
- **Manual setup:** custom prefs folder, Nerd Font, warm-burnout, Shift+Enter
- **Related:** [[Ghostty]], [[Supacode]], [[herdr]], [[Mosh]]
