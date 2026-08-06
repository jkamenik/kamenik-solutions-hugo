---
title: Tensor9
date: '2026-08-05'
lastmod: '2026-08-06'
draft: false
keywords:
- Tensor9
params:
  garden:
    kind: item
    usefulness: assess
    category: platform
    movement: No Change
    subcategories:
    - protocol
---

[Tensor9](https://tensor9.com) is an any-prem platform for software vendors. It lets a vendor deploy its full cloud-native stack into a customer's own VPC or on-prem environment, keeping data in the customer boundary while the vendor keeps centralized control and observability. We **assess** it because its install-into-customer-env, control-plane, and audited-execution model is a strong pattern for governing AI-driven execution.

## Blurb

> "Tensor9 is an enterprise any-prem platform. We enable AI vendors to deliver their product inside customer infrastructure."

## Summary

**When to use:** As a reference architecture for deploying AI and agents into customer-controlled environments, and for any-prem or private-SaaS delivery where data sovereignty is a blocker. Useful wherever AI agents process sensitive data that cannot leave the customer's boundary.

**When to skip:** When delivery is purely SaaS and no customer-boundary install is needed. Tensor9 is a deployment platform, not a product on its own.

**Key trade-offs:**

- Vendor keeps update velocity and centralized control while customer data stays in-boundary
- Control plane lives in vendor's own account; appliances reach it via outbound-only mTLS tunnel
- Fully logged, authenticated day-2 operations (remote shell, one-off commands, secrets, restarts)
- Complements Kubernetes rather than replacing it

**Related garden notes:** [[Agent Client Protocol]] (registering agent harnesses), [[Model Context Protocol]].

## Details

### Control Plane Model

Tensor9's control plane is provisioned in the vendor's own account. It orchestrates the lifecycle of every customer appliance: compile origin stack to deployable artifact, deploy, then run day-2 operations. Appliances establish an outbound-only, mutual-TLS authenticated tunnel back to the control plane, so there is no inbound network access to customer environments. Every operational action is authenticated via a permissions model and fully logged, giving an audit trail of who did what and when.

### Governance and Observability

Tensor9 aggregates metrics, logs, and traces from all distributed deployments and forwards them to existing tools (Datadog, Prometheus). Only metadata leaves customer environments; customer data never touches the control plane. This makes it a template for delivering AI observability, governance, and policy enforcement where the data lives.
