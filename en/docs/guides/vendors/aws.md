---
title: "AWS guides"
description: "Use WSO2 API Platform to govern AI traffic to Amazon Bedrock, govern APIs on Amazon API Gateway, and integrate with AWS identity and observability."
canonical_url: https://wso2.com/api-platform/docs/guides/vendors/aws/
md_url: https://wso2.com/api-platform/docs/guides/vendors/aws.md
tags:
  - guides
  - aws
  - amazon-bedrock
  - amazon-api-gateway
  - vendor-guides
author: WSO2 API Platform Documentation Team
last_updated: 2026-10-20
content_type: "overview"
---

# Build and govern AI workloads and APIs on AWS

WSO2 API Platform works alongside the AWS services you already use. Govern AI traffic to Amazon Bedrock, bring APIs running on Amazon API Gateway under one control plane, and run gateways on Amazon EKS with AWS identity and observability.

## End-to-end guides and tutorials

Step-by-step guides for AWS. Guides are part of this documentation. Tutorials are published on the WSO2 API Platform Learn Hub and written for the product version they name.

<div class="vendor-guide-list" markdown="1">

- [Discover and govern APIs from Amazon API Gateway](../gateway-federation/discover-apis-from-aws-api-gateway.md)

    Discover REST APIs on Amazon API Gateway, check compliance, and publish them to the Developer Portal.

    Guide · Amazon API Gateway

- [Use Amazon Bedrock and Bedrock Guardrails with WSO2 AI Gateway](https://wso2.com/api-platform/learn/aws-bedrock-llm-guardrails-wso2-ai-gateway/)

    Register Bedrock in AI Workspace, create an App LLM Proxy, attach a native Bedrock Guardrail, and verify request and response validation.

    Learn Hub tutorial · Amazon Bedrock

</div>

## AI Gateway with Amazon Bedrock

Route, secure, and govern traffic to foundation models on Amazon Bedrock through WSO2 AI Gateway, without changing your client applications.

<div class="vendor-cap" markdown="1">

### Amazon Bedrock as an LLM provider

Connect Amazon Bedrock with a Bedrock API key or SigV4, and manage its models and credentials centrally.

- [Use Amazon Bedrock and Bedrock Guardrails with WSO2 AI Gateway](https://wso2.com/api-platform/learn/aws-bedrock-llm-guardrails-wso2-ai-gateway/) <span class="vendor-meta">Learn Hub tutorial</span>
- [Amazon Bedrock provider](../../ai-gateway/2026.09.24/gateway-artifacts/llm-provider/supported-providers/aws-bedrock.md) <span class="vendor-meta">AI Gateway</span>

</div>

<div class="vendor-cap" markdown="1">

### AWS authentication

Sign requests with AWS Signature Version 4 (SigV4) using IAM credentials, a workload role, or cross-account role assumption.

- [Choose an authentication method](../../ai-gateway/2026.09.24/gateway-artifacts/llm-provider/supported-providers/aws-bedrock.md#choose-an-authentication-method) <span class="vendor-meta">AI Gateway</span>
- [AWS Authentication policy](https://wso2.com/api-platform/policy-hub/policies/aws-authentication) <span class="vendor-meta">Policy Hub</span>

</div>

<div class="vendor-cap" markdown="1">

### Amazon Bedrock Guardrails

Enforce the content filters, denied topics, and sensitive-information policies that you define in Amazon Bedrock on traffic through the gateway.

- [AWS Bedrock Guardrail policy](https://wso2.com/api-platform/policy-hub/policies/aws-bedrock-guardrail) <span class="vendor-meta">Policy Hub</span>
- [Guardrails catalogue](../../ai-gateway/2026.09.24/guardrails/guardrails-catalogue.md) <span class="vendor-meta">AI Gateway</span>

</div>

Routing, token limits, cost control, and the gateway's other policies work the same way for every provider. See the [AI Gateway documentation](../../ai-gateway/2026.09.24/overview.md).

!!! warning "Before you go to production"
    - **Credentials:** prefer temporary credentials or an AWS workload role. Use long-term Bedrock API keys only for exploration or development, and never give a Bedrock key to a client application.
    - **Regions and data residency:** the Region in the endpoint URL, the SigV4 signing Region, the model or inference profile, and the guardrail must all be compatible. Confirm every possible destination Region before you use cross-Region inference for regulated workloads.

## Federate with Amazon API Gateway

Manage the APIs you run on Amazon API Gateway from the WSO2 control plane. WSO2 API Platform governs only the API metadata. Consumers continue to call Amazon API Gateway directly.

<div class="vendor-cap" markdown="1">

### Discover APIs on Amazon API Gateway

Import APIs that already run on Amazon API Gateway and check their compliance.

- [Discover and govern APIs from Amazon API Gateway](../gateway-federation/discover-apis-from-aws-api-gateway.md) <span class="vendor-meta">Guide</span>
- [Discover APIs from Amazon API Gateway](../../cloud/federation/api-discovery-aws.md) <span class="vendor-meta">Cloud</span>
- [Gateway federation overview](../../cloud/federation/overview.md) <span class="vendor-meta">Cloud</span>

</div>

<div class="vendor-cap" markdown="1">

### Publish discovered APIs

Move a discovered API through its lifecycle and make it available in the Developer Portal.

- [Manage the API lifecycle](../../cloud/develop-api-proxy/lifecycle-management.md) <span class="vendor-meta">Cloud</span>
- [Discover APIs in the Developer Portal](../../cloud/devportal/discover-apis/api-search.md) <span class="vendor-meta">Cloud</span>

</div>

!!! warning "Credentials"
    The gateway connection uses the access key of an AWS Identity and Access Management (IAM) user. The guide attaches the AWS managed `AmazonAPIGatewayAdministrator` policy, which grants more than read access to your APIs. Create a dedicated IAM user for this connection only, store its secret access key in a secrets manager, rotate the key regularly, and deactivate it when you remove the gateway. Never use root account credentials.

## Run gateways on Amazon EKS

Run the gateway on your own AWS infrastructure, give it an AWS identity, and send its telemetry to AWS observability services.

<div class="vendor-cap" markdown="1">

### Deploy on Amazon EKS

The Kubernetes deployment docs aren't specific to AWS, but they apply to Amazon Elastic Kubernetes Service (Amazon EKS).

- [Kubernetes deployment modes](../../ai-gateway/2026.09.24/setup-and-deployment/kubernetes/index.md) <span class="vendor-meta">AI Gateway</span>
- [Kubernetes Operator](../../ai-gateway/2026.09.24/setup-and-deployment/kubernetes/gateway-operator.md) <span class="vendor-meta">AI Gateway</span>
- [Production deployment](../../ai-gateway/2026.09.24/setup-and-deployment/production-deployment/index.md) <span class="vendor-meta">AI Gateway</span>
- [Security hardening](../../ai-gateway/2026.09.24/setup-and-deployment/production-deployment/security-hardening.md) <span class="vendor-meta">AI Gateway</span>
- [Performance benchmarks on EKS](../../api-gateway/1.2.0/performance/overview.md) <span class="vendor-meta">API Gateway</span>

</div>

<div class="vendor-cap" markdown="1">

### Workload identity

Give each gateway workload a dedicated IAM role. For EKS, prefer EKS Pod Identity, and use IAM roles for service accounts (IRSA) as a supported alternative.

- [Default AWS credential chain](../../ai-gateway/2026.09.24/gateway-artifacts/llm-provider/supported-providers/aws-bedrock.md#default-credential-chain) <span class="vendor-meta">AI Gateway</span>
- [IAM roles for service accounts](../../ai-gateway/2026.09.24/gateway-artifacts/llm-provider/supported-providers/aws-bedrock.md#iam-roles-for-service-accounts) <span class="vendor-meta">AI Gateway</span>
- [AWS STS role assumption](../../ai-gateway/2026.09.24/gateway-artifacts/llm-provider/supported-providers/aws-bedrock.md#sts-assumerole) <span class="vendor-meta">AI Gateway</span>

</div>

<div class="vendor-cap" markdown="1">

### Amazon CloudWatch and AWS X-Ray

Export gateway logs, metrics, and traces through Fluent Bit, an OpenTelemetry Collector, or AWS Distro for OpenTelemetry (ADOT).

- [Send AI Gateway logs to CloudWatch](../../ai-gateway/2026.09.24/logging-and-tracing/gateway-logs.md#cloud-native-solutions) <span class="vendor-meta">AI Gateway</span>
- [Send AI Gateway traces to X-Ray](../../ai-gateway/2026.09.24/logging-and-tracing/tracing.md#cloud-native-tracing-solutions) <span class="vendor-meta">AI Gateway</span>
- [Send API Gateway metrics to CloudWatch](../../api-gateway/1.2.0/observability/metrics/alternative-backends.md#aws-cloudwatch) <span class="vendor-meta">API Gateway</span>
- [Send API Gateway traces to X-Ray](../../api-gateway/1.2.0/observability/tracing/alternative-backends.md#aws-x-ray) <span class="vendor-meta">API Gateway</span>

</div>

## Architecture and responsibility model

WSO2 API Platform and AWS split the work like this:

| Scenario | WSO2 role | AWS role | Runtime traffic |
| --- | --- | --- | --- |
| Amazon Bedrock through AI Gateway | Proxies and governs AI requests | Hosts the selected model and optional Bedrock guardrail | Goes through WSO2 AI Gateway to Amazon Bedrock |
| Amazon API Gateway discovery | Control plane, governance, catalog, and compliance | Hosts and runs the API | Goes directly to Amazon API Gateway |
| Gateway deployed on AWS | Runs the gateway software and policies | Provides compute, workload identity, and observability backends | Depends on the deployed gateway topology |

## Learn more

Related pages in the AWS documentation:

- [Amazon Bedrock API keys](https://docs.aws.amazon.com/bedrock/latest/userguide/api-keys.html)
- [Supported Regions and models for inference profiles](https://docs.aws.amazon.com/bedrock/latest/userguide/inference-profiles-support.html)
- [Security best practices in Amazon API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/security-best-practices.html)
- [Grant Kubernetes workloads access to AWS using service accounts](https://docs.aws.amazon.com/eks/latest/userguide/service-accounts.html)
- [Observability in the AWS Cloud Adoption Framework](https://docs.aws.amazon.com/whitepapers/latest/aws-caf-operations-perspective/observability.html)

To browse every guide by goal, see the [Guides overview](../overview.md#browse-by-use-case).
