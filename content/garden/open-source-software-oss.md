---
title: Open Source Software (OSS)
date: '2024-10-01'
lastmod: '2026-07-28'
draft: false
keywords:
- Open Source Software (OSS)
- OSS
- Open Source
params:
  aliases:
  - OSS
  - Open Source
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: Moved In
---

[Open Source Software](https://opensource.org/osd) grants rights to inspect, use, modify, and redistribute software under an open-source license. We **adopt** an OSS-first approach because modern software depends on it, with mandatory license inventory and compliance review.

## Blurb

> Open source doesn’t just mean access to the source code.

## Summary

**Why adopt:** OSS powers modern operating systems, infrastructure, development tools, libraries, and applications. Prefer viable open-source components when their license, health, security, support, and operating model satisfy the requirement.

**Required guardrails:** Maintain an up-to-date inventory of packages, versions, licenses, copyright notices, and distribution obligations. Review it continuously rather than waiting for a release or customer audit.

**When to skip:** The license conflicts with distribution or business requirements. Also skip projects with weak maintenance, unclear governance, unacceptable security posture, or lifecycle costs that exceed a supported alternative.

**Key distinction:** Source-available software is not automatically open source. An OSI-conformant license must permit redistribution, source access, derived works, and use without discrimination against people or fields of endeavor.

**Cost model:** No license fee does not mean no cost. Adoption still carries evaluation, integration, upgrades, vulnerability response, support, compliance, and exit costs.

## Details

| Decision Area | Questions |
|-------|--------|
| **License** | Is it OSI-approved? Are attribution, copyleft, patent, or network-use obligations acceptable? |
| **Health** | Are releases, maintainers, reviews, and issue response sufficient for the workload? |
| **Security** | Are advisories, patches, provenance, and vulnerability reporting handled responsibly? |
| **Governance** | Can one vendor unilaterally relicense, restrict, or abandon the project? |
| **Operations** | Who owns deployment, upgrades, backups, observability, and incident response? |
| **Exit** | Can data, configuration, and integrations move to another implementation? |

### License Families

| Family | Practical Guidance |
|-------|--------|
| Permissive | Apache 2.0, MIT, and BSD usually allow broad reuse with notices and other limited conditions |
| LGPL | Proprietary applications may link to LGPL libraries under conditions; modifications to the library remain covered |
| GPL | Internal use differs from distribution; distributing even unmodified binaries can require corresponding source and notices |
| AGPL | Modified network services can trigger source-availability obligations for remote users |
| Source-available | Code may be visible while the license restricts use, competition, or redistribution |

A conservative company policy may require legal approval or prohibit LGPL, GPL, and AGPL components. Apply the actual license version, linking model, modification status, deployment model, and distribution path. This note is operational guidance, not legal advice.

### Minimum Compliance Record

- Package name, exact version, source, and checksum
- License identifier, text, copyright notices, and attribution
- Direct and transitive dependency relationship
- Modification status and corresponding source location
- Distribution and deployment context
- Approval, exception, owner, and review date

**References**

- [The Open Source Definition](https://opensource.org/osd)
- [OSI-approved licenses](https://opensource.org/licenses)
- [GNU GPL FAQ](https://www.gnu.org/licenses/gpl-faq.html)
