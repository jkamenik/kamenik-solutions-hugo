---
title: "Gatekeeper"
date: 2024-10-01
lastmod: 2026-05-18
draft: false

keywords:
  - Gatekeeper
  - OPA Gatekeeper
  - gatekeeper

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "No Change"
    subcategories:
      - code-scanner

aliases:
  - /radar/tools/gatekeeper
---

[Gatekeeper](https://open-policy-agent.github.io/gatekeeper/) is the Kubernetes admission controller for **Open Policy Agent (OPA)**: validating and mutating webhooks plus audit scans, driven by Rego **ConstraintTemplates** and **Constraints** (CRDs). We rate it **assess**: use for **in-cluster** enforcement when **[[Policy as Code]]** rules need Rego at admission time; prefer **[[Conftest]]** (**trial**) on PRs first and **[[CEL]]** for simple native `ValidatingAdmissionPolicy` rules before operating a full OPA stack.

## Blurb

> Gatekeeper is a validating and mutating webhook that enforces CRD-based policies executed by Open Policy Agent, a policy engine for Cloud Native environments hosted by CNCF as a graduated project.

## Summary

**Where it runs:**

| Layer | Tool | When |
|-------|------|------|
| **Pre-deploy (CI)** | **[[Conftest]]** | Test manifests, Helm output, Terraform JSON on **[[Pull Request]]** |
| **Admission (cluster)** | **Gatekeeper** | Block or mutate creates/updates at the API server |
| **Admission (native)** | **[[CEL]]** | Narrow rules without OPA ops (K8s 1.26+) |
| **Audit (cluster)** | **Gatekeeper** | Report existing resources violating policy |

**What you get:**

- **Constraint library** (community templates: labels, images, security context)
- **Mutation** (patch resources to comply, use carefully)
- **External data** (call out to systems during policy eval)
- Shared **Rego** with **[[Conftest]]** when policies are designed for both paths

**Why assess (not default adopt):**

- Controller HA, webhook latency, and upgrade coupling to **[[Kubernetes]]** version
- Rego authoring and debugging cost (same as OPA elsewhere)
- Overlap with **Kyverno** (YAML policies) and **[[CEL]]** for teams that do not need full Rego

**When to assess:**

- Multi-tenant clusters with mandatory guardrails (PSA, labels, disallowed registries)
- Need audit mode to find drift on live objects
- Already **trial**ing **[[Conftest]]** and want one policy language end to end

**When to skip:**

- No Kubernetes (use **[[Conftest]]** / **[[Regula]]** on IaC only)
- Simple deny rules solvable with **[[CEL]]** and no extra controllers
- Greenfield without policy maturity (start with CI gates, not admission complexity)

## Details

| Topic | Notes |
|-------|--------|
| **Install** | Manifest or **[[Helm]]** chart (`gatekeeper-system` namespace) |
| **Policies** | Start from [Gatekeeper policy library](https://open-policy-agent.github.io/gatekeeper-library/website/) |
| **GitOps** | Constraints in Git; **[[ArgoCD]]** syncs like app manifests |
| **Performance** | Watch webhook timeouts; scope constraints to needed namespaces |
| **Mutation** | Higher blast radius than validate-only; test in dry-run/audit first |

**Garden pattern:** **adopt** **[[Policy as Code]]** as a technique; **trial** **[[Conftest]]** in CI; **assess** Gatekeeper when cluster admission must enforce the same Rego family. Compare **[[CEL]]** before committing to OPA operations.

**References**

- [Gatekeeper documentation](https://open-policy-agent.github.io/gatekeeper/)
- [OPA](https://www.openpolicyagent.org/)
