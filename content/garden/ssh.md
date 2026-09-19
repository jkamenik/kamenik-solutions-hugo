---
title: SSH
date: '2026-09-18'
lastmod: '2026-09-18'
draft: false
keywords:
- SSH
- OpenSSH
params:
  aliases:
  - OpenSSH
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: New
---

[OpenSSH](https://www.openssh.com) is the ubiquitous secure remote login protocol and tool suite. We **adopt** it as the bootstrap, key management, and file transfer layer beneath the TUI IDE stack.

## Blurb

> OpenSSH is the premier connectivity tool for remote login with the SSH protocol. It encrypts all traffic to eliminate eavesdropping, connection hijacking, and other attacks.

## Summary

Use real OpenSSH (`sshd`) on the VPS, not Tailscale SSH. [[Mosh]] bootstraps by running `mosh-server new` over SSH command execution, which Tailscale's built-in SSH does not replicate. OpenSSH also covers the scp and sftp file transfer paths.

Over the tailnet, OpenSSH traffic rides inside [[Wireguard]] with no public exposure of port 22.

## Details

- **Upstream:** https://www.openssh.com
- **Suite members:** `ssh`, `scp`, `sftp`, `ssh-keygen`, `sshd`, `ssh-agent`
- **Role:** transport bootstrap and file transfer in the TUI IDE stack
- **Required:** real `sshd` alongside the tailnet for Mosh bootstrap
- **Related:** [[Mosh]], [[Tailscale]], [[Wireguard]]
