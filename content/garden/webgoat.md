---
title: WebGoat
date: '2026-06-17'
lastmod: '2026-07-07'
draft: false
keywords:
- WebGoat
- OWASP WebGoat
params:
  aliases:
  - OWASP WebGoat
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
---

[WebGoat](https://owasp.org/www-project-webgoat/) ships guided OWASP lessons with hints, fix-it workflows, and a companion mail/file server (**WebWolf**). We **trial** it for secure-coding labs and classroom-style drills.

## Blurb

> WebGoat is a deliberately insecure web application maintained by OWASP designed to teach web application security lessons.

## Summary

**What it is:** A Java/Spring Boot training app (port 8080) plus **WebWolf** (port 9090) for email and file scenarios. Source and releases: [github.com/WebGoat/WebGoat](https://github.com/WebGoat/WebGoat).

**When to use:**

- Teaching OWASP-class flaws with step-by-step lesson text
- Java and Spring Boot secure-coding drills
- Pairing Burp or **[[Zed Attack Proxy (Zap)]]** with a localhost-bound lab
- Complementing CTF-style apps like **[[Juice Shop]]** with a classroom curriculum

**When to skip:**

- You need a modern SPA e-commerce narrative (prefer **[[Juice Shop]]**)
- You want the lightest PHP stack (prefer **[[DVWA]]**)
- You need a Django/Python lab (prefer **[[PyGoat]]**)
- You cannot disconnect or isolate the host while the lab runs

**Stack:** Java/Spring Boot (JDK 25 for current source builds per upstream README). Official paths include Docker (`webgoat/webgoat`), a browser-desktop image (`webgoat/webgoat-desktop`), and standalone JAR releases.

## Details

### Lesson Model

Lessons group into categories (for example injection, auth, client-side, general, challenge). Instructors can trim the menu with `EXCLUDE_CATEGORIES` and `EXCLUDE_LESSONS` environment variables when running the JAR or Docker image. Default configuration binds to localhost to limit exposure.

### WebGoat and WebWolf

| Service | Default port | Role |
|---------|--------------|------|
| WebGoat | 8080 | Main lesson application at `/WebGoat/` |
| WebWolf | 9090 | Companion mail and file server at `/WebWolf/` |

Some lessons require both services and matching timezone (`TZ` env var). For proxy work, upstream docs recommend custom host entries (for example `www.webgoat.local`) instead of bare `127.0.0.1`.

### Compared to Sibling Labs

| Lens | WebGoat | **[[Juice Shop]]** | **[[DVWA]]** | **[[PyGoat]]** |
|------|---------|-------------------|--------------|----------------|
| Maintainer | OWASP | OWASP | Community | Community |
| UX | Guided lesson UI | CTF scoreboard SPA | Minimal module menu | Django challenge modules |
| Stack | Java, Spring Boot | Node.js, Angular | PHP, Apache | Django, Python |
| Best fit | Classroom lesson path | Modern API/SPA drills | Web vuln fundamentals | Python/Django drills |

### Deployment Guardrails

- Disconnect from the internet or use host-only networking while the lab runs (upstream warning).
- Bind to `127.0.0.1` unless you deliberately need LAN access for a class.
- Prefer official Docker images or release JARs over stale third-party bundles.
- Reset lesson progress between sessions when you need repeatable teaching flows.
- Use only on systems you own or have explicit authorization to test.

### Install Sketch

```bash
# Docker (WebGoat + WebWolf on localhost)
docker run -it -p 127.0.0.1:8080:8080 -p 127.0.0.1:9090:9090 webgoat/webgoat
# WebGoat: http://127.0.0.1:8080/WebGoat/
# WebWolf: http://127.0.0.1:9090/WebWolf/

# Standalone JAR (see releases page for current artifact name)
export TZ=America/New_York
java -Dfile.encoding=UTF-8 -jar webgoat-2023.8.jar
```

For a full in-browser desktop with tools preinstalled, upstream documents `webgoat/webgoat-desktop` on port 3000.
