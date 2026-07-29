---
title: Second Touch Provisioning
date: '2026-01-10'
lastmod: '2026-07-29'
draft: false
keywords:
- Second Touch Provisioning
- second-touch provisioning
params:
  aliases:
  - second-touch provisioning
  garden:
    kind: subcategory
    parent_category: technique
    subcategory_slug: second-touch-provisioning
---

Under **[[Technique]]**, **Second Touch Provisioning** is the practice of configuring hosts, packages, users, and app runtime after foundation infra exists. It pairs with the **[[Provisioner]]** tool subcategory (products such as **[[Ansible]]**) and sits beside **[[First Touch Provisioning]]** (accounts, networks, clusters, managed data).

Prefer immutable images, cloud-init once, and **[[GitOps]]** on **[[Kubernetes]]** when cattle-style delivery works. Keep second-touch playbooks for bootstrap, brownfield repair, and one-time migrations. Pair provisioner products under **[[Provisioner]]** (for example **[[Ansible]]**) rather than growing long-lived pet fleets.
