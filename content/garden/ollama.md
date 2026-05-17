---
title: "Ollama"
date: 2026-05-17
lastmod: 2026-05-17
draft: false

keywords:
  - Ollama

params:
  garden:
    kind: item
    usefulness: trial
    category: platform
    movement: "New"

aliases:
  - /radar/platforms/ollama
---

[Ollama](https://ollama.com/) is a local runtime for pulling, serving, and chatting with open-weight LLMs on your machine (macOS, Linux, Windows). We rate it **trial**: the default way to run models locally for development, [[AI Agent]] backends, and privacy-sensitive experiments—pair it with agents like [[hermes-agent|Hermes]] or any OpenAI-compatible client, but expect throughput limits vs cloud APIs for heavy automation.

AI models (even when optimized) are very GPU intensive so do not expect to be able to do other things when the agent loop is running.  This limits the usefullness to only when privacy is the only concern.

## Blurb

> Get up and running with large language models locally.

## Summary

Ollama packages model weights, GPU/Metal acceleration, and a simple CLI (`ollama run`, `ollama pull`) behind a local HTTP API. Most integrations use its OpenAI-compatible endpoints so tools can swap `base_url` to `http://localhost:11434` without bespoke SDKs—aligned with our [[ADR-0001-openai-compat-over-litellm|OpenAI-compat provider]] approach for pipelines.

Strong fit on Apple Silicon and Linux workstations for iterative prompt work, offline use, and agent loops that should not send data to a hosted model. Less ideal as the sole backend for high-volume batch jobs unless you size hardware and accept latency.

## Details

- **Workflow:** install Ollama → `ollama pull <model>` → run server (often automatic) → point clients/agents at local API.
- **Models:** catalog includes Llama, Mistral, Qwen, DeepSeek, and others; tags vary by hardware (e.g. Hermes notes `deepseek` and `qwen` on Apple Silicon).
- **Integrations:** [[hermes-agent|Hermes]] and other [[AI Agent]] platforms; any OpenAI-shaped HTTP client.
- **Limits:** single-machine scale, model RAM/VRAM caps, no managed HA—use cloud providers when you need SLA, burst capacity, or centralized billing.
- **Security:** keeps prompts on-box; still vet models and plugins; not a substitute for enterprise model governance.
