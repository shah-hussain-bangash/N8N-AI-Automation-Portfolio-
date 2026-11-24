# Master Traffic Orchestrator

Scheduled Google Sheets website intake, active-site filtering, sequential GA4/GSC/uptime/PageSpeed/keyword collector calls, status aggregation, workflow logging and Slack reporting.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `Daily 06:00 Asia/Dubai`

Integrations: Google Sheets, Five n8n collector subworkflows, Slack.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- Import the five collector workflows first and reselect every Execute Workflow destination; the original installation IDs were removed.
- The schedule label says 06:00 Asia/Dubai. Verify the workflow timezone and actual schedule settings in the target installation.
- The aggregator aligns output arrays by position. Validate behavior when a collector skips a website, returns no rows or returns multiple rows.
- KPI Engine catches missing aggregate output and substitutes an empty list. Add failure visibility so collector errors are not hidden as no active websites.
- Configure the Websites schema, active filter, logging tab, Slack destination and collector credentials before activation.

## Validation

13 nodes and 13 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| Daily 06:00 Asia/Dubai | `n8n-nodes-base.scheduleTrigger` | default |
| Read Websites Tab | `n8n-nodes-base.googleSheets` | default |
| Active = TRUE | `n8n-nodes-base.filter` | default |
| KPI Engine | `n8n-nodes-base.code` | default |
| Append Workflow_Log | `n8n-nodes-base.googleSheets` | append |
| Daily Slack Summary | `n8n-nodes-base.slack` | default |
| WF-02 GA4 Daily | `n8n-nodes-base.executeWorkflow` | default |
| WF-04 GSC Daily | `n8n-nodes-base.executeWorkflow` | default |
| WF-06 Uptime | `n8n-nodes-base.executeWorkflow` | default |
| WF-07 PageSpeed | `n8n-nodes-base.executeWorkflow` | default |
| WF-08 Keyword | `n8n-nodes-base.executeWorkflow` | default |
| Combine Website Status | `n8n-nodes-base.code` | default |
| Loop Over Websites | `n8n-nodes-base.splitInBatches` | default |

## Source

Prepared from the owner-supplied export `WF-01 Master Traffic Orchestrator.json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.

## Collector import and mapping order

Import the collectors below, then import this orchestrator. In each Execute Workflow node, select the corresponding imported workflow and verify its input mapping. GitHub folder numbers and source WF labels are different identifiers; neither assigns n8n installation IDs.

| Orchestrator node | Repository project |
| --- | --- |
| WF-02 GA4 Daily | [14: GA4 Daily Collector](../14-ga4-daily-collector/README.md) |
| WF-04 GSC Daily | [15: GSC Daily Collector](../15-gsc-daily-collector/README.md) |
| WF-06 Uptime | [16: Uptime Monitor](../16-uptime-monitor/README.md) |
| WF-07 PageSpeed | [17: PageSpeed Monitor](../17-pagespeed-monitor/README.md) |
| WF-08 Keyword | [18: Keyword Ranking](../18-keyword-ranking/README.md) |

Keep the orchestrator inactive until each collector has been configured and tested independently. The separate multi-site traffic monitoring project 24 is an alternative export, not an automatically connected dependency.
