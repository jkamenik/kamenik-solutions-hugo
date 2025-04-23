---
title: 'Wireguard'
date: 2025-04-23
lastmod: 2025-04-23

# Keywords help in classifying content
keywords:
  - Wireguard
  - VPN

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: assess

    # tools, techniques, platforms, languages & frameworks
    quadrant: tools

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

[Wireguard](https://www.wireguard.com/) bills itself as a fast, modern VPN solution.  It does this by limiting interoperability to only itself, and tracking improvements via software updates.  Each client and server can only be a certain version skew from each other or communication will fail.  If you are in control of both ends of the communication and are in a place where you can keep the VPN software current then Wireguard is a viable solution.

We are glad it exists.  However, it is not a wide use case.

<!--more-->
