---
title: "ZTNA"
date: 2025-04-23
lastmod: 2026-05-18
draft: false

keywords:
  - ZTNA

params:
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: "No Change"

aliases:
  - /radar/techniques/ztna
---

Zero Trust Network Access (ZTNA) grants application-level access based on identity and policy instead of traditional perimeter VPNs. Users reach specific services through a broker after device and posture checks. Prefer ZTNA over broad VPN access for remote and third-party users; use network VPNs such as [[Tailscale]] only when you truly need layer-3 connectivity.
