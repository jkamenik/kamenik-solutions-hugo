---
title: "Juice Shop"
date: 2026-06-15
lastmod: 2026-06-22
draft: false

keywords:
  - Juice Shop
  - OWASP Juice Shop

params:
  aliases:
    - OWASP Juice Shop
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
---

[Juice Shop](https://owasp.org/www-project-juice-shop/) (OWASP Juice Shop) is a modern Node.js/Angular e-commerce app packed with deliberate security flaws. We **trial** it for CTF-style training, DAST calibration, and [[DevSecOps]] pipeline drills. Run it only in isolated lab VMs or containers, never on internet-facing hosts.

## Blurb

> Probably the most modern and sophisticated insecure web application for security trainings, awareness demos and CTFs. Also great voluntary guinea pig for your security tools and DevSecOps pipelines!

## Summary

Juice Shop wraps OWASP Top 10 and related flaws in a realistic SPA with REST APIs, scoring, and hint tiers. It targets modern stacks where [[DVWA]]'s PHP forms feel dated.

**When to use:**

- Teaching SPA and API abuse (JWT, NoSQL, GraphQL-style flows, supply chain)
- Running CTFs or awareness demos
- Benchmarking [[Zed Attack Proxy (Zap)]] or CI DAST jobs against a known-vulnerable app
- Practicing fix-it workflows on [[TypeScript]] and [[Node.js]] code

**When to skip:** you need the simplest LAMP-style modules for beginners (prefer [[DVWA]]); you cannot isolate the host from your network; you want only classic server-rendered PHP labs without client-side complexity.

**Stack:** Node.js, Express, Angular (TypeScript). Upstream docs and images live at [owasp-juice.shop](https://owasp-juice.shop) and [github.com/juice-shop/juice-shop](https://github.com/juice-shop/juice-shop).


## Details

### Challenge Model

Hundreds of categorized challenges span injection, broken auth, sensitive data exposure, XXE, access control, security misconfiguration, XSS, insecure deserialization, vulnerable components, and logging/monitoring gaps. Difficulty tiers (one star through six stars) and a scoreboard support self-paced labs and team CTFs.

### Compared to [[DVWA]]

| Lens | Juice Shop | [[DVWA]] |
|------|------------|----------|
| Stack | Node.js, Express, Angular | PHP, Apache, MariaDB |
| UX | Modern e-commerce SPA | Minimal module menu |
| Scoring | Built-in CTF scoreboard and hints | Per-module low/medium/high/impossible |
| Best fit | API/SPA and pipeline guinea pig | Classic web vuln fundamentals |

### Deployment Guardrails

- Use NAT, host-only networking, or a dedicated lab VLAN.
- Prefer official Docker images or a throwaway VM over a daily driver install.
- Reset instance state between teaching sessions when you need repeatable scores.
- Pair manual solves with DAST runs from [[Zed Attack Proxy (Zap)]] to compare human and scanner coverage.

### Install Sketch

```bash
docker run --rm -p 3000:3000 bkimminich/juice-shop
# Or clone https://github.com/juice-shop/juice-shop and follow README
```
