---
title: SupplyGoat
date: '2026-06-15'
lastmod: '2026-07-02'
draft: false
keywords:
- SupplyGoat
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
---

[SupplyGoat](https://github.com/bridgecrewio/supplygoat). We **trial** it under **[[Tool]]** in the garden.

## Blurb

> &quot;Vulnerable by Design&quot; supply chain is a learning and training project that demonstrates how common configuration errors can find their way into production cloud environments. - bridgecre...

## Summary

SupplyGoat extends Bridgecrew's Goat family beyond pure **[[IaC]]** templates (**[[TerraGoat]]**, **[[KustomizeGoat]]**, etc.) into software composition analysis (SCA). The repo mixes vulnerable lockfiles, a **[[Docker]]**file, **[[Terraform]]**, and **[[Kubernetes]]** manifests in one lab checkout.

**When to use:** teaching **[[Checkov]]** SCA and image scanning; demoing CVE findings in npm, Python, Ruby, Java, and PHP dependency trees under `package-files/`; pairing dependency drills with IaC goats in **[[DevSecOps]]** curriculum.

**When to skip:** you need a full interactive vulnerable web app (use **[[Juice Shop]]**); you only scan Terraform or K8s YAML (use IaC goats); the upstream repo stays too sparse for your exercise without custom additions.

**Repo surfaces:** `package.json` / lockfiles, `requirements.txt`, `Dockerfile`, `main.tf`, `deployment-kind.yaml`, `eks.yaml`, and multi-language samples under `package-files/`.

## Details

### Compared to IaC and Web Goats

| Lens | SupplyGoat | [[TerraGoat]] | [[Juice Shop]] |
|------|------------|---------------|----------------|
| Focus | Vulnerable dependencies and images | Cloud **[[IaC]]** misconfigs | Deliberately vulnerable web app |
| Primary scanner | **[[Checkov]]** SCA / image checks | **[[Checkov]]** IaC policies | DAST, manual exploitation |
| Ecosystems | npm, pip, Ruby, Java, PHP, Go mod | AWS/Azure/GCP templates | **[[Node.js]]** SPA |
| Best fit | Supply chain and CVE gate calibration | Pre-deploy cloud compliance | App-layer CTF labs |

### Deployment Guardrails

- Treat the repo as scan-first lab material; deploy only in isolated sandboxes if required.
- The **[[Docker]]**file uses outdated base images and vulnerable npm dependencies by design.
- Do not push built images to shared registries without explicit lab labeling.
- Tear down any **[[Kubernetes]]** or cloud resources when the exercise ends.

### Scan-First Lab Sketch
```bash
git clone https://github.com/bridgecrewio/supplygoat.git
cd supplygoat
checkov -d . --framework sca_image,sca_package
# Also scan IaC surfaces alongside SCA:
checkov -d .
```
