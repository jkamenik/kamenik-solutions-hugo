---
title: 'Jenkins'
date: 2024-04-06
lastmod: 2025-05-08
draft: true

# Keywords help in classifying content
keywords:
  - Jenkins
  - CI/CD
  - Workflow

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: hold

    # tools, techniques, platforms, languages & frameworks
    quadrant: platforms

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

> [!DANGER] Security Blackhole!
> There is no way to properly secure Jenkins and make it {{% wl "Cattle not pets" %}}.  It should not be allowed to touch production workloads, and where possible should be removed anywhere security is a concern.

Jenkins is the OSS version of Hudson and Hudson was originally designed to build Java projects.  It predates {{% wl DevOps %}} and {{% wl DevSecOps %}} by a wide margin.  While over the years there have been many attempts to make it compatible with the change in mindset, there are too many existing installations of it to make this possible.  It is software there is best avoided, and other proper {{% wl "CI-CD" %}} tools used.

If you must use Jenkins then you MUST treat it as a Pet / Snowflake and manually manage it.  I cannot tell you the number of Jenkins instances that either die on reboot, die on upgrade, or fail in a disaster recovery (DR) situation.  By the time the issue is identified it is often easier to rebuilt the entire pipeline using an appropriate tool then it is trying to make Jenkins work again.

Additionally, absolutely DO NOT use the internal sensitive information store.  First, it isn't actually secure, and is easily reversed.  Second, the information there cannot be properly managed, tokens cannot be rotated, etc...  Finally, the ID of the sensitive info is tied to machine ID.  So if the machine fails and you need to restore to a different machine then none of the ID will match and all the pipelines will have to be rebuilt by hand even if the pipeline was defined by {{% wl "Declarative IaC" IaC %}}.
