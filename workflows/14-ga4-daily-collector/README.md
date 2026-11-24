# GA4 Daily Collector

Callable collector accepts website metadata and a GA4 property ID, fetches the previous three days, formats daily metrics and upserts Google Sheets rows keyed by website and date.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `Execute Workflow Trigger`

Integrations: Google Analytics 4, Google Sheets, Parent n8n workflow.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- This export has an Execute Workflow Trigger, not a daily schedule. Configure a parent workflow to call it with Website_ID, Domain and GA4_Property_ID.
- The Google Analytics credential is not included in the exported credential inventory. Configure read access to the selected property.
- The metric and dimension selectors include empty objects. Explicitly select the intended users metric and date dimension in a compatible node version.
- Select the spreadsheet and daily tab, create the listed columns and verify upsert matching on Website_ID and Date.
- Test empty reports, unavailable properties, partial data and reruns; a status node alone is not proof that all expected daily rows were written.

## Validation

7 nodes and 6 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| Execute Workflow Trigger | `n8n-nodes-base.executeWorkflowTrigger` | default |
| Has GA4 Property? | `n8n-nodes-base.if` | default |
| GA4 Report (Last 3 Days) | `n8n-nodes-base.googleAnalytics` | default |
| Build GA4 Rows | `n8n-nodes-base.code` | default |
| Upsert GA4_Daily | `n8n-nodes-base.googleSheets` | appendOrUpdate |
| Status OK | `n8n-nodes-base.set` | default |
| Status Skipped | `n8n-nodes-base.set` | default |

## Source

Prepared from the owner-supplied export `WF-02 GA4 Daily Collector.json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
