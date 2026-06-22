---
title: "PyGoat"
date: 2026-06-17
lastmod: 2026-06-22
draft: false

keywords:
  - PyGoat

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
---

[PyGoat](https://github.com/adeyosemanputra/pygoat) is a deliberately vulnerable Django web app for OWASP Top 10 style training. We **trial** it for Python and Django secure-coding labs, manual exploitation practice, and DAST calibration. Run it only in isolated lab VMs or containers, never on internet-facing hosts.

## Blurb

> Intentionally vulnerable web application security in Django. Vulnerabilities map to the OWASP Top Ten.

## Summary

PyGoat packages common web flaws in a Django project with challenge metadata in `challenge/challenge.json` and upstream solution write-ups. It targets teams that want a Python stack lab instead of PHP ([[DVWA]]) or Node/Angular ([[Juice Shop]]).

**When to use:** teaching Django-specific mistakes alongside generic OWASP classes; practicing fixes in [[Python]] view code, ORM usage, and middleware; running a quick Docker lab on port 8000; pairing manual solves with [[Zed Attack Proxy (Zap)]] or Burp.

**When to skip:** you need a polished CTF scoreboard and hint tiers (prefer [[Juice Shop]]); you want the simplest LAMP module menu (prefer [[DVWA]]); you cannot isolate the host from your network.

**Stack:** Django, [[Python]] 3.10 or 3.11 (per upstream). Official paths include source install (`installer.sh` or `requirements.txt`), `docker pull pygoat/pygoat`, and docker-compose.


## Details

### Challenge Model

Challenges map to OWASP Top 10 themes. Definitions live in `challenge/challenge.json` and load into the database via `python manage.py populate_challenges` (documented for docker-compose as `docker compose exec web python manage.py populate_challenges`). Upstream publishes solutions under `Solutions/solution.md`.

### Compared to Sibling Labs

| Lens | PyGoat | [[Juice Shop]] | [[DVWA]] |
|------|--------|----------------|----------|
| Stack | Django, [[Python]] | Node.js, Angular | PHP, Apache, MariaDB |
| UX | Django lab modules | Modern e-commerce SPA | Minimal module menu |
| Scoring | Challenge JSON plus solutions doc | Built-in CTF scoreboard | Per-module difficulty tiers |
| Best fit | Python/Django AppSec drills | API/SPA and pipeline guinea pig | Classic web vuln fundamentals |

### Deployment Guardrails

- Use NAT, host-only networking, or a dedicated lab VLAN.
- Prefer official Docker images or a throwaway VM over a daily driver install.
- Reset database state between teaching sessions when you need repeatable challenge progress.
- Treat upstream install docs as Linux/macOS first; on Windows use Docker Desktop or WSL2.

### Install Sketch

```bash
# Fastest path: official image
docker run --rm -p 8000:8000 pygoat/pygoat:latest
# Browse http://127.0.0.1:8000

# From source
git clone https://github.com/adeyosemanputra/pygoat.git
cd pygoat
bash installer.sh
python3 manage.py migrate
python3 manage.py runserver
```

After first boot with compose, populate challenges if the UI lists none (see README `populate_challenges` step).
