---
title: Foreman
date: '2026-08-08'
lastmod: '2026-08-08'
draft: false
keywords:
- Foreman
params:
  garden:
    kind: item
    usefulness: assess
    category: platform
    movement: New
---

[Foreman](https://llmkube.com/docs/foreman) is the Kubernetes-native control plane for agentic workloads that ships as an opt-in add-on to [[LLMKube]]. It dispatches coder, verifier, and reviewer agents across a heterogeneous fleet of local LLM nodes. We **assess** it: the coder/verifier/reviewer split is a sound shape for agentic coding, but it inherits Kubernetes complexity.

## Blurb

> Foreman is the Kubernetes-native control plane for agentic workloads that ships as an opt-in add-on to LLMKube. It dispatches coder, verifier, and reviewer agents across a heterogeneous fleet of locally-hosted LLM nodes.

## Summary

Foreman models agentic coding as Kubernetes CRDs (`Workload`, `AgenticTask`, `Agent`, `FleetNode`) in its own API group and Helm chart, so it drops onto an existing LLMKube/K8s surface rather than fighting it. A `Workload` (intent + repo + issues) is decomposed by a reconciler into coder, verifier, and reviewer tasks; capability-aware scheduling claims each task on a fleet node whose hardware fits.

The v0.1 pipeline is deliberately linear: coder edits and pushes a fork branch, verifier runs a gate command (e.g. `make lint test`) and emits `GATE-PASS`/`GATE-FAIL`, and reviewers score the diff and emit `APPROVE`/`REQUEST-CHANGES`/`REJECT`. Reviewer ensembles and a coder escalation tier (fast model first, heavier model for capability failures) are first-class.

**Why the coder/verifier/reviewer split matters:** if you are going to use an agent for coding, you should think in those terms. A separate non-agentic verifier gate grounds the coder's claims, and a reviewer catches what the gate misses. In-process frameworks (CrewAI, LangGraph, AutoGen) don't solve fleet dispatch; Foreman sits between the inference engine and the application-layer agent framework.

**When to use:** you already run Kubernetes for inference and want reproducible, self-hosted agentic pipelines with humans in the loop. **When to skip:** single-machine or light setups where a simpler harness like [[Claude Code]] is enough. v0.1 lacks DAGs, best-of-N, and an autonomous planner (v0.2+).

## Details

Four CRDs: `Workload` (user intent), `AgenticTask` (dispatchable unit), `Agent` (reusable role: system prompt, tool whitelist, model endpoint, required capability), and `FleetNode` (cluster-scoped, self-registered host capability). Inference is local by default against your own InferenceServices (vLLM, llama.cpp, mlx-server); no cloud egress unless you opt in.

The verifier gate runs as a Kubernetes Job and is non-agentic. Reviewers emit structured findings against an A-through-H checklist. Escalation fires only on capability failures (NO-GO or coder-gate failure), never on INCOMPLETE or stuck-loop, since a bigger model won't fix a give-up. It assumes OpenAI `tool_calls` compatibility across inference endpoints.
