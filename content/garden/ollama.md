---
title: Ollama
date: '2026-05-17'
lastmod: '2026-07-02'
draft: false
keywords:
- Ollama
params:
  garden:
    kind: item
    usefulness: trial
    category: platform
    movement: No Change
---

[Ollama](https://ollama.com/). Is a local runtime for pulling, serving, and chatting with open-weight LLMs on your machine (macOS, Linux, Windows).

## Blurb

> Ollama is the easiest way to automate your work using open models, while keeping your data safe.

## Summary

Ollama packages model weights, GPU/Metal acceleration, and a simple CLI (`ollama run`, `ollama pull`) behind a local HTTP API. Most integrations use its OpenAI-compatible endpoints so tools can swap `base_url` to `http://localhost:11434` without bespoke SDKs, aligned with our [[ADR-0001-openai-compat-over-litellm|OpenAI-compat provider]] approach for pipelines.

Strong fit on Apple Silicon and Linux workstations for iterative prompt work, offline use, and agent loops that should not send data to a hosted model. Less ideal as the sole backend for high-volume batch jobs unless you size hardware and accept latency.

## Details

- **Workflow:** install Ollama → `ollama pull <model>` → run server (often automatic) → point clients/agents at local API.
- **Models:** catalog includes Llama, Mistral, Qwen, DeepSeek, and others; tags vary by hardware (e.g. Hermes notes `deepseek` and `qwen` on Apple Silicon).
- **Integrations:** [[hermes-agent|Hermes]] and other [[AI Agent]] platforms; any OpenAI-shaped HTTP client.
- **Limits:** single-machine scale, model RAM/VRAM caps, no managed HA. Use cloud providers when you need SLA, burst capacity, or centralized billing.
- **Security:** keeps prompts on-box; still vet models and plugins; not a substitute for enterprise model governance.
