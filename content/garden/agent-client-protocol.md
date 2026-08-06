---
title: Agent Client Protocol
date: '2026-04-20'
lastmod: '2026-08-06'
draft: false
keywords:
- Agent Client Protocol
params:
  garden:
    kind: item
    usefulness: adopt
    category: platform
    movement: No Change
    subcategories:
    - protocol
---

The agent client protocol allows separate systems to use an agent as a service in its own right. We **adopt** it under **[[Platform]]** in the garden as the protocol for registering agent harnesses.

## Summary

**When to use:** As the registration fabric for agent harnesses. ACP gives a neutral, standard handshake for any agent tool, so a control plane stays harness-agnostic: register anything, govern everything.

**When to skip:** When a simpler alternative already covers the need and there is no multi-harness registration requirement.

**Key trade-offs:**

- Harness-agnostic registration - governs any agent that speaks ACP
- Suited to governed, audited execution models where agents need to be registered and controlled before acting
- Pairs with [[Tensor9]] any-prem deployment for customer-environment control
