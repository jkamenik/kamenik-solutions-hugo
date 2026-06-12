---
title: "DevSecOps"
date: 2024-04-09
lastmod: 2026-05-18
draft: false

keywords:
  - DevSecOps

params:
  garden:
    kind: item
    usefulness: trial
    category: technique
    movement: "No Change"
---

[DevSecOps](https://www.devsecops.org/) can be thought of as [[DevOps]] with a security focus at every step. However, a better way to think about it is to treat security as a blameless iterative process.

Accept that security is an arms race against bad actors that have more time and more resources than you. Instead of throwing in the towel, or making it someone else's problem, DevSecOps is about realizing it is a risk. A risk that can be measured and acted upon in the existing [[Agile Software Development|Agile]] or [[DevOps]] process you are already following.

If you already practice DevOps and need a process to handle security concerns then DevSecOps is something to try.

Map security work to the same delivery stages you already use: plan (threat modeling, requirements), build (SAST, dependency scan), test (DAST, fuzzing), release (signing, policy gates), deploy (hardening, secrets), operate (monitoring, IR), and improve (postmortems, control updates).

## Manifesto

Taking a page out of the [[Agile Software Development|Agile Manifesto]], DevSecOps has the following manifesto:

- **Leaning in** over Always Saying “No”
- **Data & Security Science** over Fear, Uncertainty and Doubt
- **Open Contribution & Collaboration** over Security-Only Requirements
- **Consumable Security Services with APIs** over Mandated Security Controls & Paperwork
- **Business Driven Security Scores** over Rubber Stamp Security
- **Red & Blue Team Exploit Testing** over Relying on Scans & Theoretical Vulnerabilities
- **24x7 Proactive Security Monitoring** over Reacting after being Informed of an Incident
- **Shared Threat Intelligence** over Keeping Info to Ourselves
- **Compliance Operations** over Clipboards & Checklists
