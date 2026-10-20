---
title: "Azure guides"
description: "Use WSO2 API Platform to govern Azure OpenAI and Azure AI Foundry traffic, moderate content with Azure AI Content Safety, and secure APIs with Entra ID."
canonical_url: https://wso2.com/api-platform/docs/guides/vendors/azure/
md_url: https://wso2.com/api-platform/docs/guides/vendors/azure.md
tags:
  - guides
  - azure
  - azure-openai
  - entra-id
  - vendor-guides
author: WSO2 API Platform Documentation Team
last_updated: 2026-10-20
content_type: "overview"
---

# Govern Azure AI services and secure APIs with Entra ID

WSO2 API Platform works alongside the Microsoft Azure services you already use. Govern Azure OpenAI and Azure AI Foundry traffic, moderate content with Azure AI Content Safety, secure APIs with Microsoft Entra ID, and send gateway telemetry to Azure Monitor. This page brings those capabilities together in one place.

There is no Azure-specific end-to-end guide yet. Use the resources below for the capability you want to configure.

## AI Gateway with Azure OpenAI and Azure AI Foundry

Route, secure, and govern traffic to your Azure model deployments through WSO2 AI Gateway.

<div class="vendor-cap" markdown="1">

### Azure OpenAI and Azure AI Foundry as LLM providers

Point the gateway at your Azure deployment with a key that the gateway stores, so applications never hold it.

- [Azure OpenAI provider](../../ai-gateway/2026.09.24/gateway-artifacts/llm-provider/supported-providers/azure-openai.md) <span class="vendor-meta">AI Gateway</span>
- [Azure AI Foundry provider](../../ai-gateway/2026.09.24/gateway-artifacts/llm-provider/supported-providers/azure-ai-foundry.md) <span class="vendor-meta">AI Gateway</span>

</div>

<div class="vendor-cap" markdown="1">

### OpenAI-format requests

Keep clients on the OpenAI request format while the gateway routes to your Azure deployment.

- [OpenAI-format compatibility](../../ai-gateway/2026.09.24/gateway-artifacts/llm-provider/supported-providers/azure-openai.md#openai-format-compatibility) <span class="vendor-meta">AI Gateway</span>

</div>

<div class="vendor-cap" markdown="1">

### Azure cost tracking

The Azure LLM Cost policy maps each call to your deployment's pricing, so Azure spend appears alongside other providers.

- [Azure LLM Cost policy](https://wso2.com/api-platform/policy-hub/policies/azure-llm-cost) <span class="vendor-meta">Policy Hub</span>
- [Cost control and budgets](../../ai-gateway/2026.09.24/cost-control-and-budgets.md) <span class="vendor-meta">AI Gateway</span>

</div>

<div class="vendor-cap" markdown="1">

### Azure AI Content Safety

Check prompts and responses against Azure AI Content Safety categories and severity thresholds.

- [Azure Content Safety policy](https://wso2.com/api-platform/policy-hub/policies/azure-content-safety-content-moderation) <span class="vendor-meta">Policy Hub</span>
- [Guardrails catalogue](../../ai-gateway/2026.09.24/guardrails/guardrails-catalogue.md) <span class="vendor-meta">AI Gateway</span>

</div>

Routing, token limits, cost control, and the gateway's other policies work the same way for every provider. See the [AI Gateway documentation](../../ai-gateway/2026.09.24/overview.md).

## Microsoft Entra ID

Use Microsoft Entra ID (formerly Azure AD) to authorize calls to your API proxies.

<div class="vendor-cap" markdown="1">

### Authorize API calls with Entra ID tokens

Register Entra ID as a key manager, and require Entra ID tokens on your API proxies.

- [Secure API access with Azure AD](../../cloud/develop-api-proxy/authentication-and-authorization/secure-api-access-with-azure-ad.md) <span class="vendor-meta">Cloud</span>
- [Configure Azure AD as an external key manager](../../cloud/administer/configure-an-external-idp/configure-azure-ad-as-an-external-idp.md) <span class="vendor-meta">Cloud</span>

</div>

## Azure Monitor

Send the metrics and traces of a gateway you run to Azure Monitor through an OpenTelemetry Collector.

<div class="vendor-cap" markdown="1">

### Metrics and traces

Point the collector at Azure Monitor for both metrics and traces.

- [Send API Gateway metrics to Azure Monitor](../../api-gateway/1.2.0/observability/metrics/alternative-backends.md#azure-monitor) <span class="vendor-meta">API Gateway</span>
- [Send API Gateway traces to Azure Monitor](../../api-gateway/1.2.0/observability/tracing/alternative-backends.md#azure-monitor) <span class="vendor-meta">API Gateway</span>
- [Send AI Gateway traces to Azure Monitor](../../ai-gateway/2026.09.24/logging-and-tracing/tracing.md#cloud-native-tracing-solutions) <span class="vendor-meta">AI Gateway</span>

</div>

## Architecture and responsibility model

The journeys split work between WSO2 and Azure differently:

| Journey | WSO2 role | Azure role | Runtime traffic |
| --- | --- | --- | --- |
| Azure OpenAI and AI Foundry through AI Gateway | Proxies and governs LLM requests, and tracks cost per deployment | Hosts the model deployments | Goes through WSO2 AI Gateway to your Azure deployment |
| Azure AI Content Safety | Runs the guardrail and blocks or passes the request | Scores the content | The gateway calls Content Safety alongside each request |
| Entra ID and Azure Monitor | Validates Entra ID tokens and emits telemetry | Issues tokens, and stores and displays telemetry | API traffic goes through the WSO2 gateway; telemetry goes to Azure Monitor |

## Learn more

Related pages in the Microsoft documentation:

- [Microsoft Foundry](https://learn.microsoft.com/en-us/azure/foundry/what-is-foundry)
- [Azure AI Content Safety](https://learn.microsoft.com/en-us/azure/ai-services/content-safety/overview)
- [Microsoft Entra](https://learn.microsoft.com/en-us/entra/fundamentals/what-is-entra)

To browse every guide by goal, see the [Guides overview](../overview.md#browse-by-use-case).
