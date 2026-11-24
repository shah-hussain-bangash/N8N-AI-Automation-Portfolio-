# WhatsApp Template Campaigns

Manual and CSV form entry paths, phone-field mapping, WOZTELL template sends, loop delays and Google Sheets status storage.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `When clicking ‘Execute workflow’`, `On form submission`

Integrations: WOZTELL community node, Google Sheets.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- Requires the community node package @woztell-sanuker/n8n-nodes-woztell-sanuker on an n8n deployment that supports it.
- The manual path has no configured Google Sheets read node. Supply input rows or add a read step.
- WOZTELL channels and template mappings are not configured. Set template language, variables, recipient mapping and delivery-result fields.
- Test the two loop paths, CSV file parsing, rate limits and sheet update keys using a small consented test list.

## Validation

24 nodes and 13 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| When clicking ‘Execute workflow’ | `n8n-nodes-base.manualTrigger` | default |
| Edit Fields | `n8n-nodes-base.set` | default |
| Send message template | `@woztell-sanuker/n8n-nodes-woztell-sanuker.woztell` | sendTemplates |
| Loop Over Items | `n8n-nodes-base.splitInBatches` | default |
| Update row in sheet | `n8n-nodes-base.googleSheets` | update |
| Wait | `n8n-nodes-base.wait` | default |
| On form submission | `n8n-nodes-base.formTrigger` | default |
| Extract from File | `n8n-nodes-base.extractFromFile` | default |
| Edit Fields1 | `n8n-nodes-base.set` | default |
| Send message template1 | `@woztell-sanuker/n8n-nodes-woztell-sanuker.woztell` | sendTemplates |
| Loop Over Items1 | `n8n-nodes-base.splitInBatches` | default |
| Wait1 | `n8n-nodes-base.wait` | default |
| Create spreadsheet | `n8n-nodes-base.googleSheets` | default |

## Source

Prepared from the owner-supplied export `Send WhatsApp bulk template messages from Google Sheets or CSV via WOZTELL.json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
