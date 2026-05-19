---
title: "Ansible"
date: 2024-10-01
lastmod: 2026-05-18
draft: false

keywords:
  - Ansible

params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: "No Change"
    subcategories:
      - provisioner

aliases:
  - /radar/tools/ansible
---

[Ansible](https://www.ansible.com/) is agentless **[[second touch provisioning]]**: YAML playbooks drive modules over SSH from a control node (Python on the controller; remotes need only SSH and a working shell). We **adopt** it as the default when you must configure existing hosts, but treat ongoing Ansible runs as a **last resort** next to immutable images, **[[Declarative IaC]]**, and **[[GitOps]]**, because mutable SSH-managed state drifts no matter how good the tool is.

## Blurb

> Ansible is an open-source automation tool for configuration management, application deployment, and orchestration.

## Summary

**When to use:** bootstrap or repair VMs, brownfield servers, lab machines, or one-time migrations where you cannot yet replace pets with cattle. **When to avoid:** day-two loop for production fleets; prefer golden AMIs/images, **[[Terraform]]** / cloud APIs for first touch, **[[Kubernetes]]** / **[[Dev Container]]** for runtime shape, and git-reconciled desired state.

Compared to **[[Salt Stack]]** (hold) and legacy **[[Capistrano]]** (hold), Ansible wins on simplicity: no agent daemon, inventory + playbooks in git, dry-run via `ansible-playbook --check`. Controller needs SSH access (keys, ideally passwordless `sudo` on targets).

**[[DevSecOps]]** framing: provisioners are a smell. Use Ansible to reach a reproducible baseline, then stop mutating and move config into code the platform reconciles.

## Details

**Core concepts**

| Term | Meaning |
|------|---------|
| **Inventory** | Hosts and groups (`/etc/ansible/hosts`, file, or `ANSIBLE_INVENTORY`) |
| **Playbook** | YAML describing desired state for a set of hosts |
| **Task** | One module invocation with arguments (in a playbook) |
| **Module** | Unit of work; must exit 0 and emit JSON on stdout |
| **Fact** | Host metadata from setup/gathering; variables for later tasks |
| **Ad hoc** | `ansible` CLI one-liners; fine for debugging, not for production shape |

**Typical flow**

1. Install controller and collections (once)
2. SSH access and sudo policy on targets (once per host)
3. Define inventory → playbook → `ansible-playbook --check` → fix → apply
4. Retire ongoing playbook churn once images or cluster config own the shape

**Ecosystem:** Ansible Galaxy roles; **Red Hat Ansible Automation Platform** / AWX for UI, RBAC, and job scheduling when a team outgrows CLI-only workflows.

**References**

- [Quick start video](https://www.ansible.com/quick-start-video)
- [Ansible documentation](https://docs.ansible.com/)
- [Ansible book](https://www.ansible.com/ansible-book)
