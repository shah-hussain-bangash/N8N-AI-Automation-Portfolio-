# AI Post Generator and Publisher

Scheduled topic selection from Google Sheets, Gemini draft generation, Telegram approval, Unsplash image selection and LinkedIn publishing/upload steps.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `Schedule Trigger`

Integrations: Google Sheets, Google Gemini, Telegram, Unsplash, LinkedIn.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- The LinkedIn image-upload owner contains ORG_ID, and the organization destination must be configured consistently.
- Review the approval and retry paths before publishing. Attempt counters use node-scoped static data in separate nodes, so the reset node does not reset another node’s counter.
- Confirm binary upload configuration and the association between uploaded image IDs and the final LinkedIn post; exported HTTP upload settings alone do not prove media is attached.
- The topic-selection path filters unused topics, but verify a successful publication marks the selected topic as used to avoid repeated posts.
- Use private test destinations or draft-only steps to verify rejection behavior and ensure rejected drafts are not published.

## Validation

19 nodes and 17 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| Schedule Trigger | `n8n-nodes-base.scheduleTrigger` | default |
| Get row(s) in sheet | `n8n-nodes-base.googleSheets` | default |
| Choose one topic | `n8n-nodes-base.code` | default |
| Message a model | `@n8n/n8n-nodes-langchain.googleGemini` | default |
| Code in JavaScript | `n8n-nodes-base.code` | default |
| Send message and wait for response | `n8n-nodes-base.telegram` | sendAndWait |
| If | `n8n-nodes-base.if` | default |
| Create a post | `n8n-nodes-base.linkedIn` | default |
| Code in JavaScript1 | `n8n-nodes-base.code` | default |
| HTTP Request2 | `n8n-nodes-base.httpRequest` | default |
| HTTP Request3 | `n8n-nodes-base.httpRequest` | default |
| HTTP Request4 | `n8n-nodes-base.httpRequest` | default |
| Searching in Unsplash | `n8n-nodes-base.httpRequest` | default |
| Download Image | `n8n-nodes-base.httpRequest` | default |
| Check  Attempt | `n8n-nodes-base.code` | default |
| Reset Attempt Counter | `n8n-nodes-base.code` | default |
| If1 | `n8n-nodes-base.if` | default |
| Send a text message | `n8n-nodes-base.telegram` | default |
| Code in JavaScript2 | `n8n-nodes-base.code` | default |

## Source

Prepared from the owner-supplied export `Post Generator & Publisher (Test - LLG).json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
