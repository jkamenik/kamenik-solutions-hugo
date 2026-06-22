---
title: "Reasoning by analogy"
date: 2026-06-22
lastmod: 2026-06-22
draft: false

keywords:
  - Reasoning by analogy
  - Analogical Reasoning
  - Reasoning from Analogy

params:
  aliases:
    - Analogical Reasoning
    - Reasoning from Analogy
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "No Change"
    subcategories:
      - software-architecture
---

[Reasoning by analogy](https://en.wikipedia.org/wiki/Analogical_reasoning) applies a known pattern from one context to a new problem by mapping similarities between them. We **adopt** it as the default for most engineering work, including implicit cross-domain jumps when one side of the analogy is already familiar. Reach for **[[First Principles]]** when the mapping breaks or inherited defaults no longer match constraints. It belongs under **[[Technique]]** as the fast path; first principles is the deconstruction path.

## Blurb

> Analogical reasoning is the use of schema analogues, or knowledge from previous experiences, to facilitate learning in a new situation.

## Summary

Most learning in software is analogical. You hold the source pattern in memory and track only the differences in the new domain. Over time, several analogs collapse into a generalization. That consolidation is where durable knowledge forms.

| When to use | Signal |
|-------------|--------|
| **Adopt (default)** | You can name a credible source analogue and list how the target differs |
| **Assess first** | Load, compliance, team shape, or failure modes differ from the source |
| **Switch to First Principles** | Review debate centers on unstated assumptions, not pattern fit |

**Worked mental model:** **[[Continuous Integration]]** pipelines are step graphs with explicit or implicit dependencies. That maps to DAGs, then to graphs and trees used across low-level programming. One familiar domain bootstraps several others.

**Sibling technique:** **[[First Principles]]** deconstructs when analogy copies the wrong shape (microservices-by-default, cargo-cult **[[Design Pattern]]**).


## Details

### How to Apply Deliberately

1. Name the **source** you know well (prior job, **[[GitHub Actions]]** pipeline, **[[Design Pattern]]**).
2. Name the **target** problem in one sentence.
3. List **matches** (structure, constraints, failure modes).
4. List **mismatches** explicitly. Mismatches are where bugs and bad architecture hide.
5. Revisit after delivery. Merge several analogs into a general rule when the pattern repeats.

### CI Pipelines as a Bridge Pattern

Pipeline tools express work as ordered or dependent steps. That shape appears elsewhere:

| Domain | Analog to CI steps |
|--------|-------------------|
| **[[Dagu]]** / **[[Apache Airflow]]** | YAML DAG definitions |
| **[[Argo Workflows]]** | Kubernetes-native workflow graphs |
| **Compiler / linker stages** | Ordered transforms with dependencies |
| **Parse trees / ASTs** | Tree structures over graph problems |

You do not need full mastery of each target on day one. You need the analog plus the delta.

### When Analogy Fails

| False analogy | Why it breaks |
|---------------|---------------|
| "We need microservices" (copied from a unicorn) | Different load, team count, and ops maturity |
| "Use this **[[Design Pattern]]** because the book says so" | Forces don't match; ceremony without payoff |
| "Same as last project" | Compliance, data class, or SLA differ |

When the mismatch list grows faster than the match list, switch to **[[First Principles]]** and an **Assumptions** section in the design doc.

### Generalization Path

```
Single analog  →  several analogs  →  named pattern  →  garden item or design rule
```

Capture recurring generalizations as **[[Design Pattern]]** items or team standards when the same mapping appears three or more times.
