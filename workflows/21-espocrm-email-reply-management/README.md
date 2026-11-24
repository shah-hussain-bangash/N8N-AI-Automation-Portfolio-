# EspoCRM Email Reply Management

IMAP reply intake, EspoCRM lead lookup and activity logging, OpenAI intent analysis, status/task routing, Slack notifications, calendar scheduling and opportunity updates.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: 

Integrations: IMAP mailbox, EspoCRM REST API, OpenAI, Slack, Google Calendar.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- Configure CRM authentication consistently. Source header names include leading whitespace and the misspelling X-Api-Ke; use the correct header or a credential-backed connection.
- The export includes older intent branches and a unified action-routing branch. Inspect connected paths to avoid duplicate updates or notifications.
- Verify the expected n8n Code-node return shape and availability of DateTime in Prepare Action Data for the installed version.
- Test the reliable-date gate, timezone and calendar availability before allowing event creation from extracted meeting requests.
- Validate lead correlation, custom status fields, opportunity linkage, replay protection and unknown/malformed AI output with synthetic emails.

## Validation

50 nodes and 49 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| Email Trigger (IMAP) | `n8n-nodes-base.emailReadImap` | default |
| Extract Reply Details | `n8n-nodes-base.set` | default |
| Search Lead - EspoCRM | `n8n-nodes-base.httpRequest` | default |
| Lead Found? | `n8n-nodes-base.if` | default |
| Prepare EspoCRM Lead Context | `n8n-nodes-base.set` | default |
| Save Customer Reply - EspoCRM | `n8n-nodes-base.httpRequest` | default |
| Create Customer Reply Activity - EspoCRM | `n8n-nodes-base.httpRequest` | default |
| OpenAI - Analyze Reply | `@n8n/n8n-nodes-langchain.openAi` | default |
| Parse AI Response | `n8n-nodes-base.code` | default |
| Update AI Analysis - EspoCRM | `n8n-nodes-base.httpRequest` | default |
| Route by Intent | `n8n-nodes-base.switch` | default |
| Update Lead - Interested | `n8n-nodes-base.httpRequest` | default |
| EspoCRM Activity - Interested | `n8n-nodes-base.httpRequest` | default |
| Slack Notification - Interested | `n8n-nodes-base.slack` | default |
| Create EspoCRM Follow-up Task | `n8n-nodes-base.httpRequest` | default |
| Update Lead - Meeting Requested | `n8n-nodes-base.httpRequest` | default |
| Has Reliable Meeting Date? | `n8n-nodes-base.if` | default |
| Create Google Calendar Event | `n8n-nodes-base.googleCalendar` | default |
| Create EspoCRM Meeting Activity | `n8n-nodes-base.httpRequest` | default |
| Slack Notification - Meeting Scheduled | `n8n-nodes-base.slack` | default |
| Create EspoCRM Meeting Activity (No Date) | `n8n-nodes-base.httpRequest` | default |
| Slack Notification - Meeting (Confirm Time) | `n8n-nodes-base.slack` | default |
| Update Lead - Follow-up Required | `n8n-nodes-base.httpRequest` | default |
| EspoCRM Activity - Question | `n8n-nodes-base.httpRequest` | default |
| Slack Notification - Question Received | `n8n-nodes-base.slack` | default |
| Update Lead - Callback Requested | `n8n-nodes-base.httpRequest` | default |
| Create EspoCRM Call Task | `n8n-nodes-base.httpRequest` | default |
| Slack Notification - Callback Requested | `n8n-nodes-base.slack` | default |
| Update Lead - Lost | `n8n-nodes-base.httpRequest` | default |
| EspoCRM Activity - Lost | `n8n-nodes-base.httpRequest` | default |
| Update Lead - General Reply | `n8n-nodes-base.httpRequest` | default |
| EspoCRM Activity - General Reply | `n8n-nodes-base.httpRequest` | default |
| Slack Alert - Lead Not Found | `n8n-nodes-base.slack` | default |
| Update Lead - Not Interested | `n8n-nodes-base.httpRequest` | default |
| EspoCRM Activity - Not Interested | `n8n-nodes-base.httpRequest` | default |
| Slack Notification - Not Interested | `n8n-nodes-base.slack` | default |
| Slack Notification - Lost | `n8n-nodes-base.slack` | default |
| Prepare Action Data | `n8n-nodes-base.code` | default |
| Update Lead - Unified | `n8n-nodes-base.httpRequest` | default |
| Action Router | `n8n-nodes-base.switch` | default |
| Has Reliable Meeting Date?1 | `n8n-nodes-base.if` | default |
| Slack Notification - Callback Requested1 | `n8n-nodes-base.slack` | default |
| Slack Notification - General Reply | `n8n-nodes-base.slack` | default |
| Slack Notification - Meeting (Confirm Time)1 | `n8n-nodes-base.slack` | default |
| Create Google Calendar Event1 | `n8n-nodes-base.googleCalendar` | default |
| Create EspoCRM Meeting Activity1 | `n8n-nodes-base.httpRequest` | default |
| Slack Notification - Meeting Scheduled1 | `n8n-nodes-base.slack` | default |
| Get Lead for Opportunity | `n8n-nodes-base.httpRequest` | default |
| Opportunity Linked? | `n8n-nodes-base.if` | default |
| Update Opportunity from Reply | `n8n-nodes-base.httpRequest` | default |

## Source

Prepared from the owner-supplied export `Customer Email Reply Management - EspoCRM.json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
