---
title: Vagrant
date: '2024-10-01'
lastmod: '2026-07-29'
draft: false
keywords:
- Vagrant
params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: No Change
---

[Vagrant](https://developer.hashicorp.com/vagrant) manages disposable VM development environments from a `Vagrantfile`. We **adopt** it when the work needs a real guest OS, not only containers.

## Blurb

> Development Environments Made Easy. Vagrant is the command line utility for managing the lifecycle of virtual machines. Isolate dependencies and their configuration within a single disposable and consistent environment.

## Summary

**What it is:** HashiCorp CLI over providers (VirtualBox, VMware, Hyper-V, libvirt, and others). Boxes plus provisioning (shell, **[[Ansible]]**, etc.) give portable teammate parity.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Full OS / kernel needs | Drivers, systemd, nested virt, Windows guests |
| Match prod-ish VMs | Closer than **[[Docker]]** alone for some stacks |
| Teach / demo infra | Repeatable `vagrant up` labs |
| Second-touch practice | Provision guests after the box boots |

**When to skip:**

- App already runs cleanly in containers or Dev Containers
- Team has no hypervisor capacity (ARM/host friction, corporate lockdown)
- Cloud ephemeral VMs or Codespaces already solve the workspace

**Trade-offs:** Strong isolation and realism. Heavier than containers in RAM, disk, and boot time. Keep **adopt** for VM-shaped problems; prefer Docker for most app microservices.

## Details

| Concept | Notes |
|---------|--------|
| Box | Packaged base image from a catalog or custom build |
| Vagrantfile | Declarative machine, network, synced folders, provisioners |
| `vagrant up` | Create and configure the guest |

**References**

- [HashiCorp Vagrant docs](https://developer.hashicorp.com/vagrant)
- [vagrantup.com](https://www.vagrantup.com/)
