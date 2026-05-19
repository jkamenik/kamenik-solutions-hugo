---
title: "Jenkins"
date: 2024-04-06
lastmod: 2026-05-18
draft: false

keywords:
  - Jenkins

params:
  garden:
    kind: item
    usefulness: hold
    category: platform
    movement: "No Change"

aliases:
  - /radar/platforms/jenkins
---

[Jenkins](https://www.jenkins.io/)

> [!DANGER] Security Blackhole!
> There is no way to properly secure Jenkins and make it [[Cattle not pets]]. It should not be allowed to touch production workloads, and where possible should be removed anywhere security is a concern.

Jenkins is the OSS version of Hudson and Hudson was originally designed to build Java projects. It predates [[DevOps]] and [[DevSecOps]] by a wide margin. While over the years there have been many attempts to make it compatible with the change in mindset, there are too many existing installations of it to make this possible. It is software that is best avoided, and other proper [[CI-CD]] tools used.

If you must use Jenkins then you MUST treat it as a Pet / Snowflake and manually manage it. I cannot tell you the number of Jenkins instances that either die on reboot, die on upgrade, or fail in a disaster recovery (DR) situation. By the time the issue is identified it is often easier to rebuild the entire pipeline using an appropriate tool than trying to make Jenkins work again.

Additionally, absolutely DO NOT use the internal sensitive information store. First, it isn't actually secure, and is easily reversed. Second, the information there cannot be properly managed, tokens cannot be rotated, etc... Finally, the ID of the sensitive info is tied to machine ID. So if the machine fails and you need to restore to a different machine then none of the ID will match and all the pipelines will have to be rebuilt by hand even if the pipeline was defined by [[Declarative IaC]].

Instead, consider using dedicated secret management tools such as [[HashiCorp Vault]], [[AWS]] Secrets Manager, or [[Azure]] Key Vault. These tools provide robust security features, including encryption, access control, and automated secret rotation, which are essential for managing sensitive information in CI/CD pipelines.
