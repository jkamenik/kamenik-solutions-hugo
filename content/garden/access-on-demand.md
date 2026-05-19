---
title: "Access on Demand"
date: 2025-04-05
lastmod: 2026-05-18
draft: false

keywords:
  - Access on Demand

params:
  garden:
    kind: item
    usefulness: trial
    category: technique
    movement: "No Change"

aliases:
  - /radar/techniques/access-on-demand
---

[Access on Demand](https://en.wikipedia.org/wiki/Just-in-time_access)

Access on Demand (AoD, a.k.a. on-demand access) is a technique in which no standing access is granted to sensitive resources like production systems. Instead, there is a lightweight audited process to elevate access for a limited time period.

To meet even the most strict compliance frameworks all that is needed is the ability for the user to declare a reason for the increased access and the duration which is then logged. Therefore, we recommend trying this technique with your existing SSO provider to see if it is viable.

There are many ways to implement this type of system, but a common pattern that works for SAML and OIDC workflows is as follows:

1. User is granted the groups for which they get standing access and `aod_<group>` (for example `aod_aws_prod_admin`) for ones where they can increase access.
2. A system is provided that allows the user to request `aod` groups for a set duration. The reason given is logged.
3. When the request is made a new session token is provided with the new group added, and an expiry timestamp no longer than the requested duration.
4. The user uses the new token as they would any other token.
5. Each system is looking for authentication using the non-aod groups (for example `aws_prod_admin`) and thus access is granted if appropriate.
