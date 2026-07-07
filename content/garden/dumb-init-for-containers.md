---
title: Dumb-init for containers
date: '2026-05-27'
lastmod: '2026-07-02'
draft: false
keywords:
- Dumb-init for containers
params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: No Change
    subcategories:
    - containerization
aliases:
- /radar/tools/dumb-init-for-containers
---

[Dumb-init for containers](https://github.com/Yelp/dumb-init). Is a minimal PID 1 wrapper for Linux containers.

## Summary

**Problem:** Docker and Kubernetes start your app as PID 1. Without a proper init, SIGTERM handling and zombie reaping break. Shell wrappers as PID 1 add their own signal quirks.

**When to use:** production images where the entrypoint is a single binary or script; you need reliable graceful shutdown on `docker stop` / pod termination.

**When to skip:** distroless images that already ship a correct init; images using `tini` or Kubernetes `shareProcessNamespace` patterns you have standardized on.

**Usage sketch:** install the static binary in the image and set `ENTRYPOINT ["/usr/bin/dumb-init", "--"]` with `CMD` for the app.
