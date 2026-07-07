---
title: INetSim
date: '2024-10-01'
lastmod: '2026-07-07'
draft: false
keywords:
- INetSim
- Internet Services Simulation Suite
params:
  aliases:
  - Internet Services Simulation Suite
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
---

[INetSim](https://www.inetsim.org/) simulates DNS, HTTP, SMTP, and other internet services in an isolated lab so samples can run without reaching the real internet. We **assess** it for malware analysis and blue-team lab work.

## Blurb

> INetSim is a software suite for simulating common internet services in a lab environment, e.g. for analyzing the network behaviour of unknown malware samples.

## Summary

**What it is:** A GPL Perl suite that binds fake services, logs requests and replies, and produces session reports. One process replaces a patchwork of Apache, Postfix, dnsmasq, and custom scripts with unified logging.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Malware dynamic analysis | Observe DNS, download, SMTP, and C2 callback attempts safely |
| Offline or air-gapped lab VLAN | Give samples plausible "internet" without egress |
| Blue-team training | Show how droppers beacon and exfiltrate in a controlled net |
| Gateway VM in analysis topology | Pair with a sample host whose DNS resolves to the INetSim IP |

**When to skip:**

- Production service simulation or integration testing (use real stubs or **[[Docker]]** compose instead)
- Cloud-native security pipelines that already include a commercial sandbox
- Greenfield labs that need active maintenance and modern TLS interception (evaluate newer stacks first)
- Teams with no malware analysis mandate

**Trade-offs:** Last upstream release is 1.3.2 (May 2020). Still packaged in Debian and widely cited in lab guides. Perl dependency tree is dated but stable. TLS support exists for several modules; deep HTTPS inspection often needs a separate proxy in front.

## Details

### Simulated Services

| Service | Role in malware labs |
|---------|----------------------|
| DNS | Fake forward and reverse lookups; static and default answers |
| HTTP / HTTPS | Serve canned pages or capture download requests |
| SMTP / POP3 | Log mail exfiltration and spam-bot behavior |
| FTP / TFTP | File pull and drop patterns |
| NTP / Time / Daytime | Trigger time-based malware logic |
| IRC, Finger, Ident, Syslog | Legacy bot and beacon protocols |
| Dummy | Log traffic to odd ports when paired with redirection |

See the [features page](https://www.inetsim.org/features.html) for the full module list.

### Notable Features

| Feature | Use |
|---------|-----|
| **Faketime** | Return configured timestamps so time-bomb samples activate on demand |
| **Connection redirection** | IP and port rules (Linux netfilter queue) to steer traffic between modules or external sinks |
| **Session logging** | Per-connection request and reply logs plus end-of-session summary report |
| **NAT-style routing** | Make redirected traffic look like varied upstream hops (TTL tuning) |

### Typical Lab Layout

1. Isolate a sample VM on a lab VLAN with no default route to the public internet.
2. Run INetSim on a gateway host (Debian package or tarball install).
3. Point sample DNS at the INetSim IP so common hostnames resolve locally.
4. Execute the sample; collect INetSim logs and PCAP from the gateway.
5. Tear down the VLAN or revert snapshots between runs.

Run the daemon as an unprivileged dedicated user after install. Do not run the service as root.

### Limitations

- **Stale upstream:** No release since 2020; verify Perl modules and OS packages still install on your base image.
- **Scope:** Simulates protocols; it does not execute samples or replace a full sandbox VM.
- **HTTPS depth:** May need an external TLS proxy for realistic cert behavior on modern malware.
- **Platform:** Connection redirection requires Linux netfilter queue support.

### Related Garden Links

- **[[DevSecOps]]**: broader secure SDLC context; INetSim is analyst-lab tooling, not CI
- **[[Shift Left]]**: complementary axis (pre-merge scanning vs runtime sample behavior)
- **[[Docker]]**: optional packaging for lab hosts; INetSim itself is traditionally systemd on a gateway VM
