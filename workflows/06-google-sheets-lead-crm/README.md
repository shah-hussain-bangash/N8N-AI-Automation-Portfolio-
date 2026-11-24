# Google Sheets Lead CRM

Webhook intake, duplicate checks, AI classification and drafts, Slack approval, email/WhatsApp outreach, Google Sheets updates, audit logging and follow-up.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `Lead Webhook (HTTP)`

Integrations: Google Sheets, OpenAI, Slack, Brevo, WhatsApp Business, Power BI HTTP endpoint.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- The Power BI destination is a placeholder and its JSON body contains two concatenated expressions. Replace it with one valid payload and test the target schema.
- Validate webhook field casing and the classification-to-sheet mappings; the parsers do not return every field referenced downstream.
- Check Response Status has no explicit lead filter. Configure a lookup for the current lead before evaluating response status.
- Repeat Until Response / Stop is a noOp node. Implement explicit retry, suppression and stop conditions before activation.

## Validation

42 nodes and 32 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| Lead Webhook (HTTP) | `n8n-nodes-base.webhook` | default |
| Validate Required Fields | `n8n-nodes-base.if` | default |
| Send Error Alert (Slack) | `n8n-nodes-base.slack` | default |
| Search Existing Lead | `n8n-nodes-base.googleSheets` | default |
| Duplicate Found? | `n8n-nodes-base.if` | default |
| Update Existing Lead | `n8n-nodes-base.googleSheets` | appendOrUpdate |
| Create New Lead | `n8n-nodes-base.googleSheets` | append |
| AI Classify & Score Lead | `@n8n/n8n-nodes-langchain.openAi` | default |
| Parse AI Classification | `n8n-nodes-base.code` | default |
| Save AI Data to Google Sheets | `n8n-nodes-base.googleSheets` | appendOrUpdate |
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
| Update Google Sheets (Contacted) | `n8n-nodes-base.googleSheets` | appendOrUpdate |
| Push Data to Power BI | `n8n-nodes-base.httpRequest` | default |
| Log & Audit Trail | `n8n-nodes-base.googleSheets` | append |
| Wait Until Follow-up Date | `n8n-nodes-base.wait` | default |
| Check Response Status | `n8n-nodes-base.googleSheets` | default |
| Customer Replied? | `n8n-nodes-base.if` | default |
| Update Status (Interested/Meeting) | `n8n-nodes-base.googleSheets` | appendOrUpdate |
| Send Reminder Email | `n8n-nodes-base.sendInBlue` | default |
| Send Reminder WhatsApp | `n8n-nodes-base.whatsApp` | send |
| Create Call Task (in Sheet) | `n8n-nodes-base.googleSheets` | append |
| Notify Sales Team (Follow-up) | `n8n-nodes-base.slack` | default |
| Repeat Until Response / Stop | `n8n-nodes-base.noOp` | default |
| Save AI Data to Google Sheets1 | `n8n-nodes-base.googleSheets` | appendOrUpdate |
| Parse AI Classification1 | `n8n-nodes-base.code` | default |
| Generate Lead ID | `n8n-nodes-base.set` | default |

## Source

Prepared from the owner-supplied export `Complete Lead Management Automation (Google Sheets CRM).json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
