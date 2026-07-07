---
title: HCL
date: '2026-01-07'
lastmod: '2026-07-02'
draft: false
keywords:
- HCL
params:
  garden:
    kind: item
    usefulness: trial
    category: code
    movement: No Change
    subcategories:
    - language
---

[HCL](https://github.com/hashicorp/hcl). We **trial** it under **[[Code]]** in the garden.

## Blurb

> HCL is the HashiCorp configuration language. Contribute to hashicorp/hcl development by creating an account on GitHub.

## Summary

HCL grew out of a practical constraint: when [[HashiCorp]] moved its tools to [[GoLang]], embedding Go as an end-user DSL was awkward. They built a small declarative language tuned for blocks, attributes, and references. Those patterns map cleanly to infrastructure resources. It is intentionally not Turing-complete in the same way as a general programming language; expressions and functions exist, but the model stays declarative, which keeps diffs reviewable and state plans predictable.

For greenfield work outside Terraform/OpenTofu, [[YAML]] (plus optional templating via [[Helm]] or [[YAMLScript]]) or imperative/semantic IaC via [[Pulumi]] often wins on hiring surface area and license clarity. Inside an existing Terraform or OpenTofu estate, learning HCL is non-optional.

## Details

- **Syntax families:** Native HCL (`.tf`, `.hcl`), JSON syntax as an alternate encoding for the same Terraform schema, and HCL2 as the current generation used by modern Terraform.
- **Ecosystem:** Tied to [[Terraform]]; OpenTofu maintains compatible HCL. Other HashiCorp products consume HCL-shaped config but are separate adoption decisions.
- **License context:** HashiCorp's BSL shift does not change HCL's technical role but affects how aggressively to standardize on HashiCorp-only stacks versus forks or [[YAML]]-native tools.
- **When to prefer alternatives:** Kubernetes and cloud-native config ([[YAML]]), cross-cloud app-centric IaC ([[Pulumi]]), or policy expressions embedded in APIs ([[CEL]]) rather than full resource graphs.
