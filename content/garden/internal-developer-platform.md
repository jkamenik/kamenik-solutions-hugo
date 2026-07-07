---
title: Internal Developer Platform
date: '2023-07-23'
lastmod: '2026-07-07'
draft: false
keywords:
- Internal Developer Platform
params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
---

[Internal Developer Platform](https://internaldeveloperplatform.org/) is a technique we **adopt** in the garden.

## Summary

This is not so much a platform itself, but rather the realization that a platform is needed for every team. This is a loose collection of items that are glued together to lessen developer cognitive burden.

## Details

### The IDP

The IDP isn’t a single thing. And there is no off-the-shelf solution to cover every case. Instead it is a mental framework for getting the right tooling glued together in a way that facilitates developers.

The Ops team specify the resources and templates used, when the developers trigger certain actions. The Ops team has to treat the IDP like any product team would and build it based on user research, maintain it, and continually improve it.

### 3 Panes of Glass

Everyone using the IDP needs 3 panes of glass:

1. The IDE to code
2. `git` to merge/push
3. the IDP to ship

### 5 Core Components

The IDP needs to have at least 1 solution in each of the 5 areas. While multiple tools are possible in each area a goal should be the minimal set of useful tools.

### Application Configuration Management

Manage config in a dynamic, scalable, and reliable way

1. Store app config in git repos
 1. Reference template by Version (stored elsewhere as an artifact)
 2. Reference Secrets by name (not stored in git)
2. Scope should encompass all aspects of the app (external and internal)
 1. External: DNS, DBs, Platform
 2. Internal: Helm chart

### Infrastructure Orchestration

Orchestrate based on context

1. This is the pipeline tool. It has to support configuration of all the following:
 1. Pipeline - build and deployment pipelines
 2. Compute / Clusters - Setting up and making ready any compute resources
 3. 2nd touch App setup - Setting up any additional things on top of the compute
 4. Artifact Registry - Push and Pull artifacts
 5. DNS - DNS should be real
 6. Certs - Certs should be real and tied to DNS
 7. Other Resources - Anything else that might be critical

### Environment Management

Enable devs to create full envs

1. Envs should be setup the following ways:
 1. Automatic for review - It is often useful, if feasible, for an testing ENV to automatically be setup based on standard actions like a PR. This will allow the developer to have a dedicated system during development, and allow the reviewer to use that env during reviews.
 2. Self service - Next best thing where the Devs can setup their own envs as they need them.
 3. By type / Shared - Ops needs to manage a static set of envs that are maintained over time.

### Deployment Management

CD

1. Ideal development process
 1. Git push - Developer pushing code is the start CI which usually ends in Artifacts being created
 2. Automated deploy - Newly built artifacts trigger automatic deployment
 3. Trigger next steps - After the deployment is successful it should be possible to trigger the next step. That might be:
 1. Run acceptance tests
 2. Deploy to another environment
 3. Notify 3rd parties (i.e., close a maintenance window)

### Role-based Access Control
[[RBAC]]

Manage users and permissions

1. RBAC ties into Enterprise SSO. The following would be org level roles
 1. Member - any member of the team, usually they can access the stuff they setup
 2. Service Account - machine level access
 3. manager - manage other users
 4. Admin - DevOps role
2. Additionally the app or env usually has roles like
 1. Viewer - read-only access
 2. Contributor - can update config (usually also a “Member”)
 3. Owner - full admin (usually the one that deployed the env)

### Tooling

[https://internaldeveloperplatform.org/platform-tooling/](https://internaldeveloperplatform.org/platform-tooling/)
