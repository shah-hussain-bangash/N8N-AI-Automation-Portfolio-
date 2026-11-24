# AI Email Reply Management

IMAP email intake, lead lookup in Google Sheets, AI intent analysis, status routing, Slack notifications, calendar scheduling and audit logging.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: 

Integrations: IMAP mailbox, Google Sheets, OpenAI, Slack, Google Calendar.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- The source name mentions Outlook; the actual trigger is IMAP. Configure mailbox access appropriate to the provider.
- Parse AI Response accesses output text as an object. If the model returns a JSON string, parse and validate it before reading intent fields.
- The calendar event uses a fixed next-day time rather than a negotiated meeting time; verify timezone, availability and approval behavior.

## Validation

26 nodes and 22 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| IF (Is Reply?) | `n8n-nodes-base.if` | default |
| Extract Details | `n8n-nodes-base.set` | default |
| Google Sheets Get Row(s) | `n8n-nodes-base.googleSheets` | default |
| IF (Lead Found?) | `n8n-nodes-base.if` | default |
| Google Sheets Update Row | `n8n-nodes-base.googleSheets` | update |
| OpenAI - Analyze Reply | `@n8n/n8n-nodes-langchain.openAi` | default |
| Parse AI Response | `n8n-nodes-base.code` | default |
| Route by Intent | `n8n-nodes-base.switch` | default |
| Update Lead Status (Interested) | `n8n-nodes-base.googleSheets` | update |
| Slack Notification (Customer Interested) | `n8n-nodes-base.slack` | default |
| Create Call Task (Interested) | `n8n-nodes-base.googleSheets` | append |
| Update Lead Status (Meeting Requested) | `n8n-nodes-base.googleSheets` | update |
| Create Calendar Event (Meeting) | `n8n-nodes-base.googleCalendar` | default |
| Slack Notification (Meeting Requested) | `n8n-nodes-base.slack` | default |
| Update Lead Status (Question) | `n8n-nodes-base.googleSheets` | update |
| Slack Notification (Question Received) | `n8n-nodes-base.slack` | default |
| Update Lead Status (Lost) | `n8n-nodes-base.googleSheets` | update |
| Slack Notification (Not Interested) | `n8n-nodes-base.slack` | default |
| Update Lead Status (Callback Needed) | `n8n-nodes-base.googleSheets` | update |
| Create Call Task (Priority High) | `n8n-nodes-base.googleSheets` | append |
| Slack Notification (Callback Needed) | `n8n-nodes-base.slack` | default |
| Append to Audit Log | `n8n-nodes-base.googleSheets` | append |
| Notify Sales Team | `n8n-nodes-base.slack` | default |
| Slack Alert - Lead Not Found | `n8n-nodes-base.slack` | default |
| Ignore Email (Not a Reply) | `n8n-nodes-base.noOp` | default |
| Email Trigger (IMAP) | `n8n-nodes-base.emailReadImap` | default |

## Source

Prepared from the owner-supplied export `Email Reply Automation (Outlook + Google Sheets).json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
