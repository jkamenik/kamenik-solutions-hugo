---
title: "DVWA"
date: 2026-06-15
lastmod: 2026-06-22
draft: false

keywords:
  - DVWA
  - Damn Vulnerable Web Application

params:
  aliases:
    - Damn Vulnerable Web Application
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
---

[DVWA](https://github.com/digininja/DVWA) (Damn Vulnerable Web Application) is a PHP/MariaDB web app with deliberate OWASP-class flaws. We **trial** it as a legal target for manual exploitation, DAST tooling, and secure-coding lessons. Run it only in isolated lab VMs or containers, never on internet-facing hosts.

## Blurb

> Damn Vulnerable Web Application (DVWA) is a PHP/MariaDB web application that is damn vulnerable. Its main goal is to aid security professionals, web developers, students, and teachers in a controlled classroom environment.

## Summary

DVWA exposes common web vulnerabilities at four difficulty levels (low, medium, high, impossible). The UI is minimal on purpose so you focus on exploitation and remediation, not app navigation.

**When to use:** building a local security lab; practicing with [[Zed Attack Proxy (Zap)]] or Burp; teaching SQL injection, XSS, CSRF, file inclusion, and related classes; red-team or AppSec onboarding before touching production code.

**When to skip:** you need a modern stack or API-heavy scenarios (use [[Juice Shop]] instead); you cannot isolate the host from your network; you want automated pass/fail grading without manual verification.

**Stack:** PHP, Apache, MariaDB (MySQL works with extra config). Official install paths include XAMPP on a VM, Docker, or Debian-based scripts from the repo README.


## Details

### Vulnerability Modules

Typical modules include brute force, command injection, CSRF, SQL injection, XSS (reflected and stored), file upload, file inclusion (local and remote), insecure CAPTCHA, and weak session IDs. An API module adds JSON endpoints for parallel practice.

### Security Levels

| Level | Behavior |
|-------|----------|
| Low | Minimal filtering; good for first exploits |
| Medium | Partial mitigations; closer to sloppy production code |
| High | Stronger filters; requires bypass thinking |
| Impossible | Reference secure patterns after you solve lower tiers |

### Deployment Guardrails

- Use NAT or host-only networking in VirtualBox/VMware, or a dedicated lab VLAN.
- Prefer Docker or a throwaway VM over installing on a daily driver.
- Reset the database between sessions when teaching repeatable exercises.
- Pair manual labs with DAST runs from [[Zed Attack Proxy (Zap)]] to compare human findings with scanner output.

### Install Sketch

```bash
git clone https://github.com/digininja/DVWA.git
cd DVWA
# Follow README: copy config, create DB user, run setup.php, set security level
```

Docker and pre-built images are documented upstream; pick the maintained GitHub source over stale third-party bundles.
