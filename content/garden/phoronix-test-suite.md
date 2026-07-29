---
title: Phoronix Test Suite
date: '2024-10-01'
lastmod: '2026-07-28'
draft: false
keywords:
- Phoronix Test Suite
- PTS
params:
  aliases:
  - PTS
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: No Change
---

[Phoronix Test Suite](https://www.phoronix-test-suite.com/) automates reproducible hardware and system benchmarks. We **adopt** it in deployable appliances to separate product performance problems from customer-environment constraints with comparable evidence.

## Blurb

> The Phoronix Test Suite is the most comprehensive testing and benchmarking platform available that provides an extensible framework for which new tests can be easily added. The Phoronix Test Suite is focused on providing completely automated, reproducible, and turn-key deployment benchmarking.

## Summary

**When to use:** Include a focused benchmark set in downloadable or deployable appliances. Run the same profiles in known-good and customer environments to identify CPU, memory, storage, cache, or system-level constraints.

**Why adopt:** Automated dependency handling, test installation, execution, logs, and result aggregation make comparisons repeatable. The resulting evidence helps distinguish appliance defects from environmental bottlenecks.

**When to skip:** A synthetic benchmark does not represent the workload, or production constraints prohibit the test's resource use. Do not treat one score as a substitute for application-level profiling and observability.

**Test source:** OpenBenchmarking.org supplies hundreds of test profiles and suites. It also stores results and supports side-by-side comparisons.

## Details

| Profile | Signal |
|-------|--------|
| [RAMspeed](https://openbenchmarking.org/test/pts/ramspeed) | Memory bandwidth |
| [Flexible I/O Tester](https://openbenchmarking.org/test/pts/fio) | Storage throughput, latency, and I/O behavior |
| [Gzip Compression](https://openbenchmarking.org/test/pts/compress-gzip) | CPU compression performance |
| [CacheBench](https://openbenchmarking.org/test/pts/cachebench) | Memory and cache hierarchy performance |
| [stress-ng](https://openbenchmarking.org/test/pts/stress-ng) | Broad CPU, memory, I/O, and kernel stress |

| Capability | Notes |
|-------|--------|
| **Automation** | Manages dependencies, downloads, installation, execution, and result collection |
| **Evidence** | Archives system, test, and installation logs alongside benchmark results |
| **Comparison** | Produces local web reports and can compare or upload results through OpenBenchmarking.org |
| **Orchestration** | Phoromatic schedules tests and manages multiple systems from a web interface |
| **Platforms** | Supports Linux, Windows, macOS, BSD, Solaris, and GNU Hurd |

**References**

- [Phoronix Test Suite](https://www.phoronix-test-suite.com/)
- [OpenBenchmarking.org](https://openbenchmarking.org/)
- [Phoronix Test Suite on GitHub](https://github.com/phoronix-test-suite/phoronix-test-suite)
