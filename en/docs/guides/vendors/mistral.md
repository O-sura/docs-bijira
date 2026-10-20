---
title: "Mistral guides"
description: "Use WSO2 API Platform to govern traffic to Mistral AI models and to use Mistral embeddings for semantic caching and semantic guardrails."
canonical_url: https://wso2.com/api-platform/docs/guides/vendors/mistral/
md_url: https://wso2.com/api-platform/docs/guides/vendors/mistral.md
tags:
  - guides
  - mistral
  - vendor-guides
author: WSO2 API Platform Documentation Team
last_updated: 2026-10-20
content_type: "overview"
---

# Govern Mistral AI models

WSO2 API Platform works alongside Mistral AI. Govern traffic to Mistral models, centralize token and cost controls, and use Mistral embeddings for semantic caching and guardrails. This page brings those capabilities together in one place.

There is no Mistral-specific end-to-end guide yet. Use the resources below for the capability you want to configure.

## AI Gateway with Mistral models

Route, secure, and govern traffic to Mistral AI models through WSO2 AI Gateway.

<div class="vendor-cap" markdown="1">

### Mistral as an LLM provider

Connect the Mistral API with a key that the gateway stores, so applications never hold it.

- [MistralAI provider](../../ai-gateway/2026.09.24/gateway-artifacts/llm-provider/supported-providers/mistralai.md) <span class="vendor-meta">AI Gateway</span>

</div>

<div class="vendor-cap" markdown="1">

### OpenAI-format requests

Keep clients on the OpenAI request format while the gateway routes to Mistral.

- [OpenAI-format compatibility](../../ai-gateway/2026.09.24/gateway-artifacts/llm-provider/supported-providers/mistralai.md#openai-format-compatibility) <span class="vendor-meta">AI Gateway</span>

</div>

<div class="vendor-cap" markdown="1">

### Semantic caching and guardrails

Semantic caching and the semantic prompt guard compare prompts by meaning, and can use a Mistral embedding model that you set in the gateway configuration.

- [Semantic caching](../../ai-gateway/2026.09.24/semantic-caching.md) <span class="vendor-meta">AI Gateway</span>
- [Semantic prompt guard policy](https://wso2.com/api-platform/policy-hub/policies/semantic-prompt-guard) <span class="vendor-meta">Policy Hub</span>
- [Block prompt injection and unsafe requests with LLM proxy guardrails](../ai-and-mcp/block-prompt-injection-and-unsafe-requests-with-llm-proxy-guardrails.md) <span class="vendor-meta">Guide</span>

</div>

Routing, token limits, cost control, and the gateway's other policies work the same way for every provider. See the [AI Gateway documentation](../../ai-gateway/2026.09.24/overview.md).

## Architecture and responsibility model

The journeys split work between WSO2 and Mistral AI differently:

| Journey | WSO2 role | Mistral role | Runtime traffic |
| --- | --- | --- | --- |
| Applications calling Mistral models | Proxies and governs LLM requests | Hosts the models | Goes through WSO2 AI Gateway to Mistral |
| Semantic caching and guardrails | Runs the cache or guardrail policy | Returns embeddings for each prompt | The gateway calls the Mistral embeddings API alongside each request |

## Learn more

Related pages in the Mistral documentation:

- [Mistral AI documentation](https://docs.mistral.ai/)
- [Mistral models](https://docs.mistral.ai/models)
- [Mistral API reference](https://docs.mistral.ai/api)

To browse every guide by goal, see the [Guides overview](../overview.md#browse-by-use-case).
