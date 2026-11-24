# GSC Daily Collector

Callable collector accepts website metadata and a Search Console property, requests date-level search analytics for the previous three days and upserts daily Google Sheets metrics.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `Execute Workflow Trigger`

Integrations: Google Search Console API, Google Sheets, Parent n8n workflow.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- This export has an Execute Workflow Trigger, not a daily schedule. Configure a parent workflow to call it with Website_ID, Domain and GSC_Property.
- Configure the HTTP node Google API credential and grant access to the exact URL-prefix or domain property supplied by the caller.
- neverError is enabled, while Build GSC Rows treats missing rows as an empty result. Add explicit API-error and empty-data handling before reporting success.
- Select the spreadsheet and daily tab, create the listed columns and verify upsert matching on Website_ID and Date.
- Preserve CTR units consistently in reporting; the code stores the API CTR value directly without percentage conversion.

## Validation

7 nodes and 6 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| Execute Workflow Trigger | `n8n-nodes-base.executeWorkflowTrigger` | default |
| Has GSC Property? | `n8n-nodes-base.if` | default |
| GSC Search Analytics | `n8n-nodes-base.httpRequest` | default |
| Build GSC Rows | `n8n-nodes-base.code` | default |
| Upsert GSC_Daily | `n8n-nodes-base.googleSheets` | appendOrUpdate |
| Status OK | `n8n-nodes-base.set` | default |
| Status Skipped | `n8n-nodes-base.set` | default |

## Source

Prepared from the owner-supplied export `WF-04 GSC Daily Collector.json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
