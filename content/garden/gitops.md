---
title: GitOps
date: '2023-03-30'
lastmod: '2026-07-02'
draft: false
keywords:
- GitOps
params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
---

[GitOps](https://www.gitops.tech/) uses pull-request workflows to drive deployment pipelines for infrastructure, policy, and security as code. We **adopt** it under **[[Technique]]** in the garden.

## Blurb

> GitOps is Continuous Deployment for cloud native applications

## Summary

**Overview:** GitOps is a key part of [[ShiftLeft]]. The [[Pull Request]] process common for developers is an ideal way to handle *-as-code items like IaC, PaC, and SaC. A GitOps PR kicks off a [[Continuous Deployment|deployment]] pipeline the same way an application PR kicks off a build pipeline.

**When to use:** Teams already standardized on Git, PR review, and CI/CD who need traceable, attributable changes to config and environments.

## Details

### Benefits of GitOps

GitOps:

1. Is able to describe complex multi-part pipelines in a single place
2. Is able to track changes to config over time
3. Is able to fully attribute change source (i.e., committer) and approvals
4. Is able to design complex branching and merging behaviors easily
5. Has readily available tooling

### Challenges with GitOps

Even the best tool makes certain assumptions that have to be solved before the tool can be used to its full potential.

GitOps:

1. Assumes things can be described via code. This is getting better with tools like Terraform, Ansible, and Kubernetes but there are a lot of legacy out there.
2. Separates identity from actions. Again mostly a legacy thing where the legacy attributes a human user to each action. CD pipelines are always triggered by machine so there is an extra step needed for attribution.
3. Must have permissions checking and review at the file/directory level to ensure triggering by only correct folks.
 1. This is related to the separation of actions and identity. Since the CI will run using its identity and permissions GitOps can be a means to escalate privileges.
 2. The solution might be as simple as a CODEOWNERS files, or using a branch permission model.
4. Must have a good means of handling sensitive info outside of Git.
5. Should have a policy engine to check compliance.
 1. Something like Terrascan, or OpenPolicyFramework which can lint the change before it applied.
6. Makes it difficult (but not impossible) for machines to effect change.
 1. Humans are good at handling conflicts, but machines are not. Also, adding a git repo mid-stream might be unnecessary as there are usually better ways to handle state between CD stages.
