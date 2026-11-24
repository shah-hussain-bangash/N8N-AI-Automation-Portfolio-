# Multi-site Traffic Monitoring

Search Console and GA4 discovery/reporting branches, daily/weekly/monthly transformations, page/query performance, multi-account merging, sheet upserts and combined Slack summaries.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `Daily Schedule`

Integrations: Google Search Console, Google Analytics Data/Admin APIs, Google Sheets, Slack.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- The filename refers to 320 websites; this publication does not verify a tested website count, throughput or production performance.
- Configure each Google account credential, spreadsheet destination and Slack target; verify that each branch uses the intended account and property.
- Source-specific GA4 property IDs and preferred-domain mappings were replaced with placeholders. Configure the preferred-property map and the fixed-property diagnostic branch.
- Inspect overlapping discovery/reporting branches, deduplication keys, index-based response association and disconnected diagnostic nodes before scheduling.
- Verify date ranges, pagination, quotas, empty/error responses and daily/weekly/monthly upsert keys at a small scale before expanding coverage.

## Validation

85 nodes and 89 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| Daily Schedule | `n8n-nodes-base.scheduleTrigger` | default |
| List Search Console Sites | `n8n-nodes-base.httpRequest` | default |
| Split Search Console Sites | `n8n-nodes-base.code` | default |
| Fetch Search Analytics | `n8n-nodes-base.httpRequest` | default |
| Clean Daily KPIs | `n8n-nodes-base.code` | default |
| Fetch Page Performance | `n8n-nodes-base.httpRequest` | default |
| Clean Page Performance | `n8n-nodes-base.code` | default |
| Page_Performance | `n8n-nodes-base.googleSheets` | appendOrUpdate |
| Daily_Summary | `n8n-nodes-base.googleSheets` | appendOrUpdate |
| Fetch Weekly Analytics | `n8n-nodes-base.httpRequest` | default |
| Clean Weekly KPIs | `n8n-nodes-base.code` | default |
| Weekly_Summary | `n8n-nodes-base.googleSheets` | appendOrUpdate |
| Fetch Monthly Analytics | `n8n-nodes-base.httpRequest` | default |
| Clean Monthly KPIs | `n8n-nodes-base.code` | default |
| Monthly_Summary | `n8n-nodes-base.googleSheets` | appendOrUpdate |
| Fetch Query Performance | `n8n-nodes-base.httpRequest` | default |
| Clean Query Performance | `n8n-nodes-base.code` | default |
| Query_Performance | `n8n-nodes-base.googleSheets` | appendOrUpdate |
| Build Slack Daily Summary | `n8n-nodes-base.code` | default |
| List Search Console Sites 2 | `n8n-nodes-base.httpRequest` | default |
| Split Search Console Sites2 | `n8n-nodes-base.code` | default |
| Fetch Search Analytics2 | `n8n-nodes-base.httpRequest` | default |
| Clean Daily KPIs2 | `n8n-nodes-base.code` | default |
| Merge | `n8n-nodes-base.merge` | default |
| Remove Daily Duplicates | `n8n-nodes-base.code` | default |
| Fetch Weekly Analytics2 | `n8n-nodes-base.httpRequest` | default |
| Clean Weekly KPIs2 | `n8n-nodes-base.code` | default |
| Merge Weekly Accounts2 | `n8n-nodes-base.merge` | default |
| Remove Weekly Duplicates2 | `n8n-nodes-base.code` | default |
| List Search Console Sites3 | `n8n-nodes-base.httpRequest` | default |
| Split Search Console Sites3 | `n8n-nodes-base.code` | default |
| Fetch Search Analytics3 | `n8n-nodes-base.httpRequest` | default |
| Clean Daily KPIs3 | `n8n-nodes-base.code` | default |
| Fetch Weekly Analytics3 | `n8n-nodes-base.httpRequest` | default |
| Clean Weekly KPIs3 | `n8n-nodes-base.code` | default |
| Fetch Monthly Analytics2 | `n8n-nodes-base.httpRequest` | default |
| Fetch Page Performance2 | `n8n-nodes-base.httpRequest` | default |
| Fetch Query Performance2 | `n8n-nodes-base.httpRequest` | default |
| Clean Monthly KPIs2 | `n8n-nodes-base.code` | default |
| Clean Page Performance2 | `n8n-nodes-base.code` | default |
| Clean Query Performance2 | `n8n-nodes-base.code` | default |
| Merge Monthly Accounts2 | `n8n-nodes-base.merge` | default |
| Merge Page Performance Accounts2 | `n8n-nodes-base.merge` | default |
| Merge Query Accounts2 | `n8n-nodes-base.merge` | default |
| Remove Monthly Duplicates2 | `n8n-nodes-base.code` | default |
| Remove Page Performance Duplicates2 | `n8n-nodes-base.code` | default |
| Remove Query Duplicates2 | `n8n-nodes-base.code` | default |
| Fetch Monthly Analytics3 | `n8n-nodes-base.httpRequest` | default |
| Clean Monthly KPIs3 | `n8n-nodes-base.code` | default |
| Fetch Page Performance3 | `n8n-nodes-base.httpRequest` | default |
| Clean Page Performance3 | `n8n-nodes-base.code` | default |
| Fetch Query Performance3 | `n8n-nodes-base.httpRequest` | default |
| Clean Query Performance3 | `n8n-nodes-base.code` | default |
| Merge1 | `n8n-nodes-base.merge` | default |
| Merge2 | `n8n-nodes-base.merge` | default |
| Merge3 | `n8n-nodes-base.merge` | default |
| Merge4 | `n8n-nodes-base.merge` | default |
| Merge5 | `n8n-nodes-base.merge` | default |
| HTTP Request | `n8n-nodes-base.httpRequest` | default |
| Fetch GA4 Daily Traffic | `n8n-nodes-base.httpRequest` | default |
| Clean GA4 Daily Traffic | `n8n-nodes-base.code` | default |
| GA4 Daily Summary | `n8n-nodes-base.googleSheets` | appendOrUpdate |
| GA4 Weekly Summary | `n8n-nodes-base.googleSheets` | appendOrUpdate |
| GA4 Monthly Summary | `n8n-nodes-base.googleSheets` | appendOrUpdate |
| List GA4 Properties | `n8n-nodes-base.httpRequest` | default |
| Split GA4 Properties | `n8n-nodes-base.code` | default |
| List GA4 Data Streams | `n8n-nodes-base.httpRequest` | default |
| Clean GA4 Properties & Streams | `n8n-nodes-base.code` | default |
| Fetch GA4 Daily All Properties | `n8n-nodes-base.httpRequest` | default |
| Clean GA4 Daily All Properties | `n8n-nodes-base.code` | default |
| Fetch GA4 Weekly All Properties | `n8n-nodes-base.httpRequest` | default |
| Clean GA4 Weekly All Properties | `n8n-nodes-base.code` | default |
| Fetch GA4 Monthly All Properties | `n8n-nodes-base.httpRequest` | default |
| Clean GA4 Monthly All Properties | `n8n-nodes-base.code` | default |
| Select Preferred GA4 Properties | `n8n-nodes-base.code` | default |
| List GA4 Properties1 | `n8n-nodes-base.httpRequest` | default |
| GA4 Build Slack Daily Summary | `n8n-nodes-base.code` | default |
| Merge6 | `n8n-nodes-base.merge` | default |
| Build Combined Slack Report | `n8n-nodes-base.code` | default |
| HTTP Request — Slack | `n8n-nodes-base.httpRequest` | default |
| Fetch GA4 Realtime Test | `n8n-nodes-base.httpRequest` | default |
| Code in JavaScript | `n8n-nodes-base.code` | default |

## Source

Prepared from the owner-supplied export `320 Websites Traffics Monitoring.json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
