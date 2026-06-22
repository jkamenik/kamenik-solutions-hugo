---
title: "CfnGoat"
date: 2026-06-15
lastmod: 2026-06-22
draft: false

keywords:
  - CfnGoat

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
---

[CfnGoat](https://github.com/bridgecrewio/cfngoat) is Bridgecrew's "Vulnerable by Design" AWS CloudFormation template repository. It ships a single `cfngoat.yaml` stack full of intentional misconfigurations for IaC security training. We **trial** it as a legal target for **[[Checkov]]** scans on raw CloudFormation and **[[Shift Left]]** pipeline drills. Never deploy it in production AWS accounts or beside sensitive workloads.

## Blurb

> Cfngoat is one of Bridgecrew's "Vulnerable by Design" Infrastructure as Code repositories, a learning and training project that demonstrates how common configuration errors can find their way into production cloud environments.

## Summary

CfnGoat sits in Bridgecrew's IaC Goat family alongside **[[TerraGoat]]**, **[[CdkGoat]]**, and **[[BicepGoat]]**. Use it when the lab artifact is a CloudFormation YAML template, not Terraform HCL or CDK synth output.

**When to use:** calibrating **[[Checkov]]** on CloudFormation directly; teaching **[[Policy as Code]]** gates before stack deploy; teams that still author CFN templates or review **[[CdkGoat]]** synth output as CFN.

**When to skip:** you cannot isolate a disposable AWS account; you need Terraform labs (use **[[TerraGoat]]**); you need CDK-specific synth workflows (use **[[CdkGoat]]**); you need app-layer vuln targets only (use **[[DVWA]]** or **[[Juice Shop]]**).

**Deploy model:** `aws cloudformation create-stack` against `cfngoat.yaml` (expect 5+ minutes). Change `--stack-name` and `Environment` to run multiple sandboxes.


## Details

### Compared to Sibling Goats

| Lens | CfnGoat | [[TerraGoat]] | [[CdkGoat]] |
|------|---------|---------------|-------------|
| IaC format | CloudFormation YAML | Terraform (HCL) | AWS CDK to synthesized CFN |
| Scan target | `cfngoat.yaml` in repo | `.tf` files and plans | `cdk.out/*.template.json` |
| Cloud focus | AWS | AWS, Azure, GCP | AWS |
| Best fit | Direct CFN template scanning | Multi-cloud Terraform training | CDK pipeline gates |

### Deployment Guardrails

- Use a dedicated sandbox AWS account with no production data.
- Upstream warns that stack create deploys intentionally insecure resources.
- Pass `CAPABILITY_NAMED_IAM`; set a strong `Password` parameter per README.
- Delete stacks when the lab ends (`aws cloudformation delete-stack` or console).
- Scan locally with **[[Checkov]]** before any stack create.

### Scan-First Lab Sketch

```bash
git clone https://github.com/bridgecrewio/cfngoat.git
cd cfngoat
checkov -f cfngoat.yaml
# Optional: create-stack in sandbox only after reviewing findings
```
