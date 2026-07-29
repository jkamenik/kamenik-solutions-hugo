---
title: Provisioner
date: '2025-12-30'
lastmod: '2026-07-29'
draft: false
keywords:
- Provisioner
params:
  garden:
    kind: subcategory
    parent_category: tool
    subcategory_slug: provisioner
---

Under **[[Tool]]**, **Provisioner** groups products that configure or converge hosts and services after (or beside) foundation infra. Typical examples are agentless config managers and CM tools such as **[[Ansible]]**. Tag a product here when the note is about the tool you run to apply desired state on targets, not about the practice itself.

Sibling techniques: **[[First Touch Provisioning]]** (accounts, networks, clusters as code) and **[[second touch provisioning]]** (host and app configuration). Prefer golden images, **[[Declarative IaC]]**, and **[[GitOps]]** for day-two production where possible; keep provisioner tools for bootstrap, brownfield, and migration.
