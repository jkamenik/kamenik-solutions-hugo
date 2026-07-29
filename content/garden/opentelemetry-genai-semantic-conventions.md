---
title: OpenTelemetry GenAI Semantic Conventions
date: '2026-07-29'
lastmod: '2026-07-29'
draft: false
keywords:
- OpenTelemetry GenAI Semantic Conventions
- GenAI Semantic Conventions
- OTel GenAI SemConv
params:
  aliases:
  - GenAI Semantic Conventions
  - OTel GenAI SemConv
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: New
    subcategories:
    - specification
    - ai-techniques
---

[OpenTelemetry GenAI Semantic Conventions](https://github.com/open-telemetry/semantic-conventions-genai) is the OTel repo for GenAI and MCP telemetry conventions (spans, metrics, events). We **assess** it for standardizing agent and LLM observability before vendor schemas lock in.

## Blurb

> Semantic Conventions for Generative AI (GenAI), including spans, metrics, and events for GenAI clients, MCP (Model Context Protocol), and provider-specific conventions (OpenAI, etc.).

## Summary

**When to use:** instrumenting LLM clients, agents, embeddings, retrieval, or **[[Model Context Protocol]]** servers/clients with **[[OpenTelemetry]]**. Prefer these attribute names when backends or SDKs already expose `gen_ai.*` / `mcp.*`.

**When to skip:** pure classic service telemetry with no GenAI path. Stay on core [semantic-conventions](https://github.com/open-telemetry/semantic-conventions) until you emit model or agent signals.

**Trade-offs:** docs mark GenAI conventions **Development**, so names and required fields can still change. The GenAI model lives in this repo (Weaver-managed) and links a pinned core semconv version for shared attributes.

**Pairs with:** OTel SDKs and Collector pipelines; provider-specific docs (OpenAI, Anthropic, Bedrock, Azure AI Inference); MCP host observability.

## Details

- **Signals:** GenAI events, exceptions, metrics, model spans, and agent spans; plus MCP-specific conventions.
- **Providers:** technology-specific pages for Anthropic, Azure AI Inference, AWS Bedrock, and OpenAI.
- **Layout:** human docs under `docs/`; YAML model under `model/`; reference implementations under `reference/`.
- **Upstream:** extends core OpenTelemetry semantic conventions; not a replacement for the main semconv repo.
- **Status:** document status is Development as of note creation (2026-07-29). Re-check before treating attribute sets as stable contracts.
