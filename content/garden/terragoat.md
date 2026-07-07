---
title: TerraGoat
date: '2026-06-15'
lastmod: '2026-07-02'
draft: false
keywords:
- TerraGoat
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
---

[TerraGoat](https://github.com/bridgecrewio/terragoat). We **trial** it under **[[Tool]]** in the garden.

## Blurb

> TerraGoat is Bridgecrew&#39;s &quot;Vulnerable by Design&quot; Terraform repository. TerraGoat is a learning and training project that demonstrates how common configuration errors can find their wa...

## Summary

TerraGoat follows the Goat tradition (**[[DVWA]]**, **[[Juice Shop]]**) for cloud infrastructure: real **[[IaC]]** files with CIS, PCI, and provider-specific misconfigurations baked in.

**When to use:** calibrating **[[Checkov]]** or other IaC scanners; teaching **[[Policy as Code]]** and **[[DevSecOps]]** gates on **[[Pull Request]]**s; demoing how misconfigurations reach prod if scans are skipped.

**When to skip:** you cannot isolate a disposable cloud account; you need app-layer vuln labs only (use **[[DVWA]]** or **[[Juice Shop]]**); you lack budget to tear down AWS/Azure/GCP resources after the lab.

**Cloud modules:** separate Terraform roots under `terraform/aws/`, `terraform/azure/`, and `terraform/gcp/`. Use remote state (S3 backend documented upstream) and `terraform destroy` when finished.

## Details

### Compared to Web Goat Projects

| Lens | TerraGoat | [[DVWA]] / [[Juice Shop]] |
|------|-----------|---------------------------|
| Surface | **[[Terraform]]** for AWS, Azure, GCP | Deliberately vulnerable web apps |
| Risk | Real cloud resources in your account | Local VM or container |
| Scanner pairing | **[[Checkov]]**, pre-commit, CI IaC gates | **[[Zed Attack Proxy (Zap)]]**, DAST |
| Best fit | IaC and cloud misconfiguration training | OWASP-style app exploitation |

### Deployment Guardrails

- Use a dedicated sandbox account or subscription with no production data.
- Set `TF_VAR_environment` to isolate multiple stacks in one account.
- Read upstream warnings before `terraform apply`: resources are intentionally insecure.
- Run `terraform destroy` when the lab ends; verify the account is clean.
- Scan the repo locally with **[[Checkov]]** before any apply to practice catch-before-deploy.

### Scan-First Lab Sketch
```bash
git clone https://github.com/bridgecrewio/terragoat.git
cd terragoat
checkov -d terraform/aws/
# Optional: apply in sandbox only after reviewing findings
```
