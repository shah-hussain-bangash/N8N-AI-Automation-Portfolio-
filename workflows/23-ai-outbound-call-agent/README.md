# AI Outbound Call Agent

Google Sheets lead trigger, contacted-state check, ElevenLabs/Twilio outbound-call request, delayed conversation lookup and lead-row update.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `New Lead Found`

Integrations: Google Sheets, ElevenLabs conversational AI, Twilio phone integration.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- Configure ELEVENLABS_AGENT_ID and ELEVENLABS_PHONE_NUMBER_ID workflow variables, API credentials and the lead spreadsheet schema.
- A fixed delay precedes conversation lookup. Add completion polling, timeouts and explicit failed-call handling before relying on the summary.
- Test loop continuation on contacted, successful and failed leads; a branch ending early can stop further lead processing.
- Validate phone normalization, duplicate-call prevention and row matching. Use only a consented test number for runtime verification.
- Publishing this export does not execute calls; no call was made during preparation.

## Validation

8 nodes and 9 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| New Lead Found | `n8n-nodes-base.googleSheetsTrigger` | default |
| Loop Over Leads | `n8n-nodes-base.splitInBatches` | default |
| Already Contacted? | `n8n-nodes-base.if` | default |
| Start AI Call (ElevenLabs + Twilio) | `n8n-nodes-base.httpRequest` | default |
| Wait For Call To End | `n8n-nodes-base.wait` | default |
| Get Call Summary & Outcome | `n8n-nodes-base.httpRequest` | default |
| Update Lead Row | `n8n-nodes-base.googleSheets` | update |
| Skip This Lead | `n8n-nodes-base.noOp` | default |

## Source

Prepared from the owner-supplied export `AI Outbound Call Agent (ElevenLabs + Twilio).json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
