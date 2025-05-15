---
title: 'Access on Demand'
date: 2025-04-05
lastmod: 2025-05-10

aliases:
  - aod
  - oda
  - on-demand-access

# Keywords help in classifying content
keywords:
  - Access on Demand
  - Authorization
  - Permissions

params:
  aka:
    - AoD

  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: trial

    # tools, techniques, platforms, languages & frameworks
    quadrant: techniques

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

Access on Demand (AoD, a.k.a On-demand Access) is a technique in which no standing access is granted to sensitive resources like production systems.  Instead there is a lightweight audited process to elevate access for a limited time period.

To meet even the most strict compliance frameworks all that is needed is the ability for the user to declare a reason for the increased access and the duration which is then logged.  Therefore we recommend trying this technique with your existing SSO provider to see if it is viable.

<!--more-->

There are many ways to implement this type of system, but a common that works for SAML and OIDC workflows is as follows:

1. User is granted the groups for which they get standing access and `aod_<group>` (for example `aod_aws_prod_admin`) for ones where they can increase access.
2. A system is provided that allows the user to requires `aod` groups for a set time using.  The reason given is logged.
3. When the request is made a new session token is provided with the new group added, and a expiry timestamp no longer then the requested duration.
4. The user uses the new token as they would any other token.
5. Each system is looking for authentication using the non-aod groups (for example `aws_prod_admin`) and thus access is granted if appropriate.
