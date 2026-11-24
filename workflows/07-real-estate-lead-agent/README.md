# Real Estate Lead Agent

Webhook intake, Odoo duplicate handling, AI agents with structured output schemas, Slack approval, Brevo email and placeholder WhatsApp/Power BI HTTP steps.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `Lead Webhook`

Integrations: Odoo, OpenAI, Slack, Brevo, WhatsApp Cloud API, Power BI HTTP endpoint.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- Slack Lead Summary is configured as a conversation get operation, rather than sending a summary. Review the intended behavior.
- The WhatsApp and Power BI destinations are source placeholders. Configure credentials, resource IDs and request schemas.
- Verify that the Odoo record being updated exists for every intake path; duplicate checking alone does not establish record creation.
- Configure memory session keys for webhook requests and confirm structured parser outputs match downstream mappings.

## Validation

21 nodes and 20 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| Lead Webhook | `n8n-nodes-base.webhook` | default |
| Validate Required Fields | `n8n-nodes-base.if` | default |
| Duplicate Lead Check | `n8n-nodes-base.odoo` | default |
| Duplicate Found? | `n8n-nodes-base.if` | default |
| Update Existing Lead | `n8n-nodes-base.odoo` | update |
| AI Classification | `@n8n/n8n-nodes-langchain.agent` | default |
| Classification Model | `@n8n/n8n-nodes-langchain.lmChatOpenAi` | default |
| Classification Schema | `@n8n/n8n-nodes-langchain.outputParserStructured` | default |
| AI Draft Response | `@n8n/n8n-nodes-langchain.agent` | default |
| Draft Model | `@n8n/n8n-nodes-langchain.lmChatOpenAi` | default |
| Draft Schema | `@n8n/n8n-nodes-langchain.outputParserStructured` | default |
| Slack Lead Summary | `n8n-nodes-base.slack` | get |
| Human Approval | `n8n-nodes-base.slack` | sendAndWait |
| Approved? | `n8n-nodes-base.if` | default |
| Send Brevo Email | `n8n-nodes-base.sendInBlue` | default |
| Send WhatsApp | `n8n-nodes-base.httpRequest` | default |
| Update Odoo CRM | `n8n-nodes-base.odoo` | update |
| Power BI Push | `n8n-nodes-base.httpRequest` | default |
| Return to Sales Team | `n8n-nodes-base.slack` | default |
| Invalid Lead - Missing Fields | `n8n-nodes-base.noOp` | default |
| Simple Memory | `@n8n/n8n-nodes-langchain.memoryBufferWindow` | default |

## Source

Prepared from the owner-supplied export `Real Estate Lead Automation.json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
