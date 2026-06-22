---
title: "PM2"
date: 2026-05-28
lastmod: 2026-06-22
draft: false

keywords:
  - PM2

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
aliases:
  - /radar/tools/pm2
---

[PM2](https://pm2.keymetrics.io/) is a production process manager for Node.js and Bun with a built-in load balancer. We rate it **trial** as a **[[Tool]]** for bare-metal or single-host Node deployments. It keeps apps alive, reloads without downtime, and handles logs and startup scripts when you are not yet on **[[Docker]]** or **[[Kubernetes]]**.

## Blurb

> PM2 is a production process manager for Node.js/Bun applications with a built-in load balancer. It allows you to keep applications alive forever, to reload them without downtime and to facilitate common system admin tasks.

## Summary

**What it is:** PM2 daemonizes Node.js and Bun apps, restarts them on crash, and exposes CLI and ecosystem-file config for multiple apps and environments. Cluster mode forks workers across CPU cores and load-balances HTTP, TCP, and UDP traffic. `pm2-runtime` is the container-friendly entrypoint that runs in the foreground.

**When to use:**

- One or a few Node services on a Linux VM or VPS
- Zero-downtime reloads, log aggregation under `~/.pm2/logs`, and `pm2 startup` integration with systemd or init
- A simple deploy path before adopting full **[[DevOps]]** orchestration

**When to skip:** Workloads already packaged in **[[Docker]]** with a proper init or orchestrated by **[[Kubernetes]]**. Teams standardized on systemd unit files only. Polyglot fleets where a Node-specific manager adds little value.

**Ecosystem file:** `ecosystem.config.js` (or JSON/YAML) declares app names, scripts, env vars, cluster settings, and deploy targets in one place.


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
