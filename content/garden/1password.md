---
title: 1Password
date: '2026-07-29'
lastmod: '2026-07-29'
draft: false
keywords:
- 1Password
- 1Password Extended Access Management
- 1Password XAM
params:
  aliases:
  - 1Password Extended Access Management
  - 1Password XAM
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: No Change
---

[1Password](https://1password.com/) is a password, secrets, and access-management platform for people, machines, and AI agents. We **adopt** it as the default personal vault, and as the password manager to recommend when a company has none yet.

## Blurb

> One secure platform for humans, AI agents, and machines. Unified Access is built to discover, secure, and audit.

## Summary

**What it is:** End-to-end encrypted vaults plus enterprise products: password manager, privileged access, credential broker for agents/workloads, and SaaS Manager (ex-Trelica). CLI (`op inject`, `op run`) covers many inject-into-process needs without a second secrets tool.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Personal / family vault | Default choice; strong UX, passkeys, travel modes |
| Company with no password manager | Recommend 1Password; then stay in that ecosystem |
| Business shared vaults | Admin policies, SSO hooks, team vaults |
| Shadow IT / SaaS sprawl | SaaS Manager for discovery, spend, and access workflows |
| Agent / machine credentials | Credential Broker and privileged access; also `op` for local/CI |

**When to skip:**

- Org already standardized on another vault (Bitwarden, Keeper, and so on). Stay in their ecosystem.
- Hard requirement for self-hosted secrets with no vendor trust boundary
- Pure Git-encrypted files with no vault product: **assess** **[[SOPS (Secret OPerationS)]]** only when there is no password manager

**Trade-offs:** Excellent polish and CLI for day-to-day secrets. SaaS dependency and expanding XAM surface area. Once chosen, prefer `op` over stacking **[[SOPS (Secret OPerationS)]]** for the same job.

## Details

| Product area | Notes |
|--------------|--------|
| Personal / Business Password Manager | Default vault recommendation |
| CLI | `op inject` for inline refs; `op run` for subprocess env |
| Privileged Access | Just-in-time / just-enough access patterns |
| Credential Broker | Runtime credentials for agents and workloads |
| SaaS Manager | App discovery, governance, spend (Trelica tech) |

**References**

- [1password.com](https://1password.com/)
- [1Password CLI](https://developer.1password.com/docs/cli/)
- [Company / leadership](https://1password.com/company)
- [Trelica acquisition (Jan 2025)](https://1password.com/blog/1password-acquires-trelica)
