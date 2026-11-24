# Keyword Ranking Collector

Callable SerpApi search compares organic results with a supplied domain and stores the matched rank, keyword and date in Google Sheets.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `Execute Workflow Trigger`

Integrations: SerpApi, Google Sheets, Parent n8n workflow.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- Requires Website_ID, Domain and Keyword from a caller and a configured SerpApi credential.
- The matching code uses substring matching on normalized URLs. Validate hostname matching to avoid unrelated domains or paths being counted.
- The search requests up to 100 results, but this does not establish a complete or location-independent ranking. Configure country, language and device as required.
- Explicitly handle provider errors, empty results and unavailable ranking separately; the source parser sets ok=true even when no result is found.

## Validation

7 nodes and 6 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| Execute Workflow Trigger | `n8n-nodes-base.executeWorkflowTrigger` | default |
| Has Keyword? | `n8n-nodes-base.if` | default |
| SERP Search | `n8n-nodes-base.httpRequest` | default |
| Find Rank | `n8n-nodes-base.code` | default |
| Upsert Keyword_Rankings | `n8n-nodes-base.googleSheets` | appendOrUpdate |
| Status OK | `n8n-nodes-base.set` | default |
| Status Skipped | `n8n-nodes-base.set` | default |

## Source

Prepared from the owner-supplied export `WF-08 Keyword Ranking.json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
