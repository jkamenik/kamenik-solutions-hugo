---
title: "Dumb-init for containers"
date: 2026-05-27
lastmod: 2026-05-27
draft: false

keywords:
  - Dumb-init for containers

params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: "New"
    subcategories:
      - containerization

aliases:
  - /radar/tools/dumb-init-for-containers
---

[dumb-init](https://github.com/Yelp/dumb-init) is a minimal PID 1 wrapper for Linux containers. It forwards signals to the child process and reaps zombie processes. We **adopt** it when the main process is not designed to run as init (most app images).

## Blurb

> dumb-init runs as PID 1, acting like a simple init system. It launches a single process and then proxies all received signals to a session rooted at that child process.

## Summary

**Problem:** Docker and Kubernetes start your app as PID 1. Without a proper init, SIGTERM handling and zombie reaping break. Shell wrappers as PID 1 add their own signal quirks.

**When to use:** production images where the entrypoint is a single binary or script; you need reliable graceful shutdown on `docker stop` / pod termination.

**When to skip:** distroless images that already ship a correct init; images using `tini` or Kubernetes `shareProcessNamespace` patterns you have standardized on.

**Usage sketch:** install the static binary in the image and set `ENTRYPOINT ["/usr/bin/dumb-init", "--"]` with `CMD` for the app.
