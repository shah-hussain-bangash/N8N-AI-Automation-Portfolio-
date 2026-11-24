# Website Uptime Monitor

Callable monitor checks a supplied domain with an HTTP timeout, classifies response status and logs downtime alerts to Google Sheets.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `Execute Workflow Trigger`

Integrations: HTTP website checks, Google Sheets, Parent n8n workflow.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- Requires a caller supplying Website_ID and Domain. It has no independent schedule.
- Test DNS, TLS, timeout and network exceptions; neverError handles HTTP status responses but does not establish recovery from every transport failure.
- Classify Status sets ok=true even when the site is Down. The parent must distinguish collector execution status from website availability.
- The alert-write branch may change the output shape. Normalize the returned status before relying on the parent aggregator.

## Validation

7 nodes and 6 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| Execute Workflow Trigger | `n8n-nodes-base.executeWorkflowTrigger` | default |
| Has Domain? | `n8n-nodes-base.if` | default |
| Check Website | `n8n-nodes-base.httpRequest` | default |
| Classify Status | `n8n-nodes-base.code` | default |
| Is Down? | `n8n-nodes-base.if` | default |
| Log Downtime Alert | `n8n-nodes-base.googleSheets` | append |
| Status Skipped | `n8n-nodes-base.set` | default |

## Source

Prepared from the owner-supplied export `WF-06 Uptime Monitor.json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
