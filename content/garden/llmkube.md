---
title: LLMKube
date: '2026-08-08'
lastmod: '2026-08-08'
draft: false
keywords:
- LLMKube
params:
  garden:
    kind: item
    usefulness: assess
    category: platform
    movement: New
---

[LLMKube](https://llmkube.com) is a Kubernetes operator for self-hosted LLM inference. It runs vLLM, llama.cpp, and TGI on NVIDIA, Apple Silicon, and AMD hardware. We **assess** it because it promises production-grade orchestration for local models, which our estate lacks.

## Blurb

> Run production LLMs on your own hardware. A Kubernetes operator for self-hosted LLM inference: vLLM, llama.cpp, and TGI on NVIDIA, Apple Silicon, and AMD.

## Summary

LLMKube positions itself as the orchestration layer for self-hosted LLM inference, filling the gap between Docker Compose setups and full SaaS inference providers. It models LLM workloads as Kubernetes CRDs (`Model`, `InferenceService`) and supports HPA autoscaling driven by real inference metrics, multi-GPU sharding, and Grafana dashboards. Its companion harness, Foreman, runs agentic coder/verifier/reviewer agents on the same fleet with a "honest-verdict" gate.

**When to use:** you already run Kubernetes and want reproducible, autoscaled inference across a heterogeneous fleet (NVIDIA + Apple Silicon + AMD) under a single model key. **When to skip:** single-machine or minimal setups where [Ollama](https://llmkube.com) or Docker Compose is simpler, or when you want managed inference.

Key trade-offs: it adds Kubernetes operational overhead for the autoscaling and multi-runtime benefits. It is open source (Apache-2.0) and community-built by Defilan Technologies. Related garden notes: [[Kubernetes]], [[Ollama]].

## Details

LLMKube supports GGUF models from HuggingFace with automatic download and caching. It ships a CLI (`llmkube deploy`) that renders deployment as YAML. Runtime support: vLLM, TGI, llama.cpp, plus a bring-your-own path. Hardware: CUDA 13 and NVIDIA Blackwell, Apple Silicon (MLX/mlx-server), AMD (Vulkan). The Foreman harness is a Kubernetes-native control plane that dispatches coding agents across the fleet and has agents open their own pull requests.
