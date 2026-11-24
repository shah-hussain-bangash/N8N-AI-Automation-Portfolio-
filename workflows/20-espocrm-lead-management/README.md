# EspoCRM Lead Management

Webhook lead intake, EspoCRM duplicate search and create/update operations, OpenAI classification and drafting, Slack approval, email/WhatsApp outreach, notes and opportunity-related steps.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `Lead Webhook (HTTP)`

Integrations: EspoCRM REST API, OpenAI, Slack, Brevo, WhatsApp Business.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- Replace CRM host, API-key placeholders, sender details and account resources. The source mixes HTTP and HTTPS addresses; use a verified secure destination.
- EspoCRM Update Lead1 contains a fixed source record ID, now a placeholder. Replace it with the intended current-record expression before testing.
- Search Opportunity - EspoCRM requests a Lead resource. Verify the opportunity lookup, linkage and update mappings against your actual schema.
- Confirm every communication path is gated by the intended approval result and that rejected requests do not send messages.
- Custom lead fields, opportunity fields and activity payloads must exist in the target EspoCRM installation.

## Validation

34 nodes and 34 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| Lead Webhook (HTTP) | `n8n-nodes-base.webhook` | default |
| Validate Required Fields | `n8n-nodes-base.if` | default |
| Send Error Alert (Slack) | `n8n-nodes-base.slack` | default |
| Duplicate Found? | `n8n-nodes-base.if` | default |
| AI Classify & Score Lead | `@n8n/n8n-nodes-langchain.openAi` | default |
| AI Generate Draft | `@n8n/n8n-nodes-langchain.openAi` | default |
| Parse AI Draft | `n8n-nodes-base.code` | default |
| Post Lead Summary (Slack) | `n8n-nodes-base.slack` | default |
| Sales Manager Approval | `n8n-nodes-base.slack` | sendAndWait |
| Approved? | `n8n-nodes-base.if` | default |
| Return to Sales Team (Slack) | `n8n-nodes-base.slack` | default |
| Notify Sales Team (Rejected) | `n8n-nodes-base.slack` | default |
| Assign Lead | `n8n-nodes-base.set` | default |
| Send Email (Brevo) | `n8n-nodes-base.sendInBlue` | default |
| Merge Comms | `n8n-nodes-base.merge` | default |
| Send WhatsApp | `n8n-nodes-base.whatsApp` | default |
| Track Delivery Status | `n8n-nodes-base.set` | default |
| Parse AI Classification1 | `n8n-nodes-base.code` | default |
| Generate Lead ID | `n8n-nodes-base.set` | default |
| Wait | `n8n-nodes-base.wait` | default |
| Set Source Information | `n8n-nodes-base.set` | default |
| Search Existing Lead - EspoCRM | `n8n-nodes-base.httpRequest` | default |
| Create New Lead - EspoCRM | `n8n-nodes-base.httpRequest` | default |
| Update Existing Lead - EspoCRM | `n8n-nodes-base.httpRequest` | default |
| Prepare Draft Data | `n8n-nodes-base.set` | default |
| EspoCRM Update Lead | `n8n-nodes-base.httpRequest` | default |
| Prepare EspoCRM Record ID | `n8n-nodes-base.set` | default |
| Create EspoCRM Activity Log | `n8n-nodes-base.httpRequest` | default |
| Search Opportunity - EspoCRM | `n8n-nodes-base.httpRequest` | default |
| EspoCRM Update Lead1 | `n8n-nodes-base.httpRequest` | default |
| Opportunity Exists? | `n8n-nodes-base.if` | default |
| Create Opportunity - EspoCRM | `n8n-nodes-base.httpRequest` | default |
| Link Opportunity to Lead | `n8n-nodes-base.httpRequest` | default |
| Update Existing Opportunity - EspoCRM | `n8n-nodes-base.httpRequest` | default |

## Source

Prepared from the owner-supplied export `EspoCRM Lead Managament Automation Complete.json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
