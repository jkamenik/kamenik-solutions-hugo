---
title: "CdkGoat"
date: 2026-06-15
lastmod: 2026-06-22
draft: false

keywords:
  - CdkGoat

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
---

[CdkGoat](https://github.com/bridgecrewio/cdkgoat) is Bridgecrew's "Vulnerable by Design" AWS CDK application. It synthesizes intentionally misconfigured CloudFormation for IaC security training. We **trial** it as a legal target for **[[Checkov]]** scans on `cdk synth` output and **[[Shift Left]]** pipeline drills. Never deploy it in production AWS accounts or beside sensitive workloads.

## Blurb

> CdkGoat is Bridgecrew's "Vulnerable by Design" AWS CDK repository. CdkGoat is a learning and training project that demonstrates how common configuration errors can find their way into production cloud environments.

## Summary

CdkGoat sits in Bridgecrew's IaC Goat family alongside **[[TerraGoat]]** and **[[BicepGoat]]**. Use it when the lab stack is AWS CDK (Python), not raw Terraform or Bicep.

**When to use:** teaching **[[Checkov]]** on synthesized CloudFormation when source repos have no `.yaml` templates; calibrating CI gates for **[[CDKs]]**-based teams; demoing build-time scanning before `cdk deploy`.

**When to skip:** you cannot isolate a disposable AWS account; you need Terraform labs (use **[[TerraGoat]]**); your org avoids CDK for new work (**[[CDKs]]** is **hold** here, but the goat still helps scanner tuning).

**Workflow:** `cdk synth` produces `cdk.out/cdkgoat.template.json`; scan that artifact with **[[Checkov]]** before optional sandbox deploy.


## Details

### Compared to [[TerraGoat]]

| Lens | CdkGoat | [[TerraGoat]] |
|------|---------|---------------|
| IaC style | AWS CDK (**[[Imperative IaC]]**, **[[Python]]**) | Terraform (HCL) |
| Scan target | Synthesized CloudFormation JSON | `.tf` files and plans |
| Cloud focus | AWS | AWS, Azure, GCP |
| Best fit | CDK pipeline and synth-time gates | Multi-cloud Terraform training |

### Deployment Guardrails

- Use a dedicated sandbox AWS account with no production data.
- Upstream warns that `cdk deploy` creates intentionally insecure resources.
- Rename S3 buckets and other global names if deploy fails on collisions.
- Run `cdk destroy` when the lab ends; verify the account is clean.
- Scan after `cdk synth` even when you skip deploy.

### Scan-First Lab Sketch

```bash
git clone https://github.com/bridgecrewio/cdkgoat.git
cd cdkgoat
python -m venv .env && source .env/bin/activate
pip install -r requirements.txt
npm install -g aws-cdk
cdk synth
checkov -f cdk.out/cdkgoat.template.json
```
