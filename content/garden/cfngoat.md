---
title: CfnGoat
date: '2026-06-15'
lastmod: '2026-07-02'
draft: false
keywords:
- CfnGoat
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
---

[CfnGoat](https://github.com/bridgecrewio/cfngoat). Is Bridgecrew's "Vulnerable by Design" AWS CloudFormation template repository.

## Summary

**Garden stance:** We **trial** CfnGoat for our estate.

**Key points:** ### Compared to Sibling Goats

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
