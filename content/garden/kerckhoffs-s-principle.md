---
title: "Kerckhoffs's principle"
date: '2024-10-01'
lastmod: '2026-07-28'
draft: false
keywords:
- "Kerckhoffs's principle"
- Kerckhoffs Principle
- Kerkhoffs Principle
params:
  aliases:
  - Kerckhoffs Principle
  - Kerkhoffs Principle
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - specification
---

[Kerckhoffs's principle](https://en.wikipedia.org/wiki/Kerckhoffs%27s_principle) says a secure system stays secure when its design is public and only key material stays secret. We **adopt** it as the baseline for crypto choices, threat modeling, and security review.

## Blurb

> It must not be required to be secret, and it should be able to fall into the hands of the enemy without inconvenience.

## Summary

**What it is:** A design rule from Auguste Kerckhoffs (1883). Security must not depend on hiding the mechanism. Secrecy belongs in keys, credentials, and other rotatable secret material.

**When to use:** Any time you pick or review encryption, signing, authentication, or access controls. Treat full design disclosure as the threat-model default. Claude Shannon's shorthand applies: assume the enemy knows the system.

**When to skip:** Never as a principle. You may still layer operational controls (firewalls, access logging, least privilege). Those are defense in depth, not a substitute for a secret algorithm.

| Situation | Garden stance |
|-----------|---------------|
| Choosing TLS ciphers, password hashes, or token formats | **Adopt** public, peer-reviewed algorithms |
| Vendor offers a proprietary cipher you cannot audit | **Hold** until they publish specs or you can verify independently |
| Hiding an API path or admin URL as the main control | Reject. That is security through obscurity, not Kerckhoffs |

**Pairs with:** **[[Zero Trust Network Architecture]]** (verify every request; do not trust network location). **[[Policy as Code]]** and **[[SARIF]]** for repeatable gates in **[[DevSecOps]]** pipelines.

## Details

### Origin and Formulation

Auguste Kerckhoffs published six desiderata for military ciphers in 1883. The principle above is the second. Modern crypto restates it as: only the key should be secret; the algorithm may be public.

### What Counts as the Key

| Secret material | Role |
|-----------------|------|
| Symmetric encryption key | Protects confidentiality |
| Private signing key | Proves origin and integrity |
| API token, session secret, password | Authenticates a caller or user |
| Salt (password storage) | Not a key. May be public; it slows rainbow tables |

Operational secrecy still matters. You do not publish live key material. Kerckhoffs asks what happens **if** the mechanism is exposed, not whether you should leak keys on purpose.

### Modern Applications

- **TLS and messaging:** AES, ChaCha20, RSA, and ECDSA are public algorithms. Security rests on key length and correct implementation.
- **Password storage:** bcrypt, scrypt, and Argon2 are public. The hash output can leak; the password must not.
- **App secrets:** Rotate API keys and signing secrets. Do not rely on an obscure endpoint path as the control.

### Common Violations

- Custom or "military grade" ciphers with no public specification
- Hard-coded secrets in source control (the secret became part of a brittle, non-rotatable design)
- Security reviews that assume attackers will never see your architecture diagrams
- Treating "no one knows our URL" as equivalent to authentication

### Related Ideas (Not the Same)

- **Security through obscurity:** Hiding design or implementation instead of using sound crypto. Fragile when the secret leaks once.
- **Defense in depth:** Multiple independent controls. Compatible with Kerckhoffs when each layer does not depend on hidden mechanics.
- **[[Zero Trust Network Architecture]]:** Architectural stance that complements algorithmic openness. Assume breach; verify explicitly.
