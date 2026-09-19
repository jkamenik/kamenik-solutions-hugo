---
title: Mosh
date: '2026-09-18'
lastmod: '2026-09-18'
draft: false
keywords:
- Mosh
params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: New
---

[Mosh](https://mosh.org) is the mobile shell for interactive remote sessions that survive roaming and flaky links. We **adopt** it for interactive TUI IDE sessions over the tailnet.

## Blurb

> Mosh is a replacement for interactive SSH terminals. It's more robust and responsive, especially over Wi-Fi, cellular, and long-distance links.

## Summary

Use Mosh when the interactive session must survive IP changes, Wi-Fi to cellular handoffs, client sleep, or packet loss. It authenticates through SSH once, then runs a UDP session on ports 60000 to 61000.

Mosh has no scrollback because it syncs visible screen state. [[herdr]] holds the buffer server-side, so the stack is covered.

Over the tailnet, Mosh's UDP addresses the [[Tailscale]] IP and rides inside [[Wireguard]], so the VPS never publicly exposes the mosh ports.

Keep [[SSH]] for bootstrap and file transfer.

## Details

- **Upstream:** https://mosh.org
- **Role:** interactive transport in the TUI IDE stack
- **Bootstrap:** `mosh-server new` runs over SSH command execution, so real OpenSSH is required
- **Locales:** mosh-server refuses to run without a UTF-8 locale
- **Caveat:** no scrollback; herdr owns the buffer
- **Related:** [[SSH]], [[herdr]], [[Tailscale]], [[Wireguard]]
