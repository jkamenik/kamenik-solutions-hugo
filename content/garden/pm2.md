---
title: PM2
date: '2026-05-28'
lastmod: '2026-07-02'
draft: false
keywords:
- PM2
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
aliases:
- /radar/tools/pm2
---

[PM2](https://pm2.keymetrics.io/). Is a production process manager for Node.js and Bun with a built-in load balancer.

## Summary

**Garden stance:** We **trial** PM2 for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

| Feature | Notes |
|---------|--------|
| **Process control** | `pm2 start`, `stop`, `restart`, `reload`, `delete`; list with `pm2 ls` |
| **Cluster mode** | `-i max` or a fixed instance count; use `reload` (not `restart`) for zero-downtime |
| **Logs** | `pm2 logs`, rotation via `pm2-logrotate`; files under `~/.pm2/logs` |
| **Monitoring** | `pm2 monit` for CPU, memory, and request stats in the terminal |
| **Boot persistence** | `pm2 save` plus `pm2 startup` generates OS startup hooks |
| **Containers** | `pm2-runtime` replaces `node` as PID 1 friendly foreground runner |
| **Deploy** | Built-in multi-host deploy (Git-based); lighter than **[[Capistrano]]** but overlaps |

**12-factor fit:** aligns with disposability and logs-as-streams from **[[12 Factor App]]**. Pair with env-based config, not checked-in secrets.

**PM2+:** optional hosted monitoring from the Keymetrics team. The open-source runtime stands alone without a subscription.

**Alternatives:** **[[Docker]]** plus Compose or Swarm for packaging and restart policy. **[[Kubernetes]]** for multi-node scheduling. Plain systemd units when you want no extra dependency and only one or two services.

**References**

- [PM2 Runtime overview](https://pm2.io/docs/runtime/overview/)
- [PM2 GitHub repository](https://github.com/Unitech/pm2)
- [Ecosystem file](https://pm2.keymetrics.io/docs/usage/application-declaration/)
