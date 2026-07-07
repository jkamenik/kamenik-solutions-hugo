---
title: InsecureBank v2
date: '2026-06-17'
lastmod: '2026-07-02'
draft: false
keywords:
- InsecureBank v2
- Android InsecureBank v2
- InsecureBankv2
params:
  aliases:
  - Android InsecureBank v2
  - InsecureBankv2
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
---

[InsecureBank v2](https://github.com/dineshshetty/Android-InsecureBankv2). Is a deliberately vulnerable Android banking app with a Python 2 AndroLab back-end server.

## Blurb

> Vulnerable Android application for developers and security enthusiasts to learn about Android insecurities - dineshshetty/Android-InsecureBankv2

## Summary

**Garden stance:** We **trial** InsecureBank v2 for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

### Vulnerability Coverage

The README lists flaws across Android components, storage, crypto, and transport. Representative categories:

| Area | Examples |
|------|----------|
| Components | Flawed broadcast receivers, intent sniffing and injection, vulnerable activities, insecure content providers |
| Client hardening | Root and emulator detection bypass, application patching, runtime manipulation, debuggable flag |
| Data handling | Local encryption issues, insecure SD card storage, pasteboard and keyboard cache leaks, backup exposure |
| Network and auth | Insecure HTTP, weak authorization, parameter manipulation, username enumeration, hardcoded secrets |
| Other | Insecure WebView, weak cryptography, insecure logging, developer backdoors, weak change-password flow |

Work-in-progress items (per upstream) include path traversal, local SQL injection, lock-screen bypass, and location spoofing.

### Lab Topology

1. Install `InsecureBankv2.apk` on an emulator or rooted lab device.
2. Start AndroLabServer from `AndroLabServer/` on a host the emulator can reach.
3. Confirm host-to-emulator networking (adb shell, netcat) before debugging app login failures.
4. Log in with demo accounts from the README (for example `dinesh` / `Dinesh@123$` or `jack` / `Jack@123$`).

The repo includes `Walkthroughs/` and `Usage Guide.pdf` for guided exploitation paths.

### Compared to Web Labs

| Lens | InsecureBank v2 | [[Juice Shop]] / [[DVWA]] |
|------|-----------------|---------------------------|
| Surface | Android APK plus mobile API | Browser and HTTP APIs |
| Skills | Reverse engineering, Frida, adb | Burp, [[Zed Attack Proxy (Zap)]], browser devtools |
| Server | Python 2 AndroLabServer (lab only) | PHP/Node stack in container or VM |
| Best fit | Mobile AppSec and MASTG drills | OWASP Top 10 web fundamentals |

### Deployment Guardrails

- Use a dedicated emulator or lab phone, not a daily driver with personal data.
- Keep AndroLabServer on a host-only or lab VLAN interface.
- Treat demo credentials and hardcoded secrets as intentional; never reuse those patterns in real apps.
- Expect Python 2 and older Android SDK assumptions; pin emulator images that match upstream docs.
- Reset app data and server DB between teaching sessions for repeatable scores.

### Install Sketch
```bash
git clone https://github.com/dineshshetty/Android-InsecureBankv2.git
cd Android-InsecureBankv2/AndroLabServer
pip install -r requirements.txt   # Python 2 environment
python app.py                     # start back-end; note bind address for emulator
adb install ../InsecureBankv2.apk
```
See `Usage Guide.pdf` in the repo for full server and emulator networking steps.
