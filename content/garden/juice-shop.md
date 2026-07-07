---
title: Juice Shop
date: '2026-06-15'
lastmod: '2026-07-02'
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
    movement: No Change
---

[Juice Shop](https://owasp.org/www-project-juice-shop/). (OWASP Juice Shop) is a modern Node.js/Angular e-commerce app packed with deliberate security flaws.

## Blurb

> Probably the most modern and sophisticated insecure web application for security trainings, awareness demos and CTFs. Also great voluntary guinea pig for your security tools and DevSecOps pipelines!

## Summary

**Garden stance:** We **trial** Juice Shop for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

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
