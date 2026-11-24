# PageSpeed Performance Monitor

Callable mobile PageSpeed Insights check extracts performance score, first contentful paint and largest contentful paint, then upserts a dated Google Sheets row.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `Execute Workflow Trigger`

Integrations: Google PageSpeed Insights, Google Sheets, Parent n8n workflow.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- Requires a caller supplying Website_ID and Domain. Configure the API credential and destination spreadsheet/tab.
- The HTTP node enables neverError. Check for API errors and missing Lighthouse results before treating a run as successful.
- Review the final Status OK mapping against the parser ok flag; a completed request may still contain no score.
- Verify quotas, request timeouts and upsert matching with one test domain before scheduling a large list.

## Validation

7 nodes and 6 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| Execute Workflow Trigger | `n8n-nodes-base.executeWorkflowTrigger` | default |
| Has Domain? | `n8n-nodes-base.if` | default |
| PageSpeed Insights | `n8n-nodes-base.httpRequest` | default |
| Extract Scores | `n8n-nodes-base.code` | default |
| Upsert PageSpeed | `n8n-nodes-base.googleSheets` | appendOrUpdate |
| Status OK | `n8n-nodes-base.set` | default |
| Status Skipped | `n8n-nodes-base.set` | default |

## Source

Prepared from the owner-supplied export `WF-07 PageSpeed Monitor.json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
