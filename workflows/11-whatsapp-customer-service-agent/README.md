# WhatsApp Customer Service Agent

Incoming WhatsApp messages feed a Gemini agent with conversation memory and Google Sheets tools; agent replies are sent back to the originating contact.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `WhatsApp Trigger`

Integrations: WhatsApp Business, Google Gemini, Google Sheets tools.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- Get Inventory, Get FAQ and Post Orders are configured with resource=spreadsheet and create-style fields, not inventory/FAQ row reads or order-row writes. Configure their intended operations, schemas and destinations.
- The memory expression uses json["messages[0]"].from, while other nodes use json.messages[0].from. Verify the event shape and correct the session key before activation.
- The agent assumes a text message is present. Add handling for status updates, media and malformed events.
- Configure WhatsApp webhook verification, credentials, phone number ID and approved messaging behavior.

## Validation

8 nodes and 7 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| WhatsApp Trigger | `n8n-nodes-base.whatsAppTrigger` | default |
| AI Agent | `@n8n/n8n-nodes-langchain.agent` | default |
| Google Gemini Chat Model | `@n8n/n8n-nodes-langchain.lmChatGoogleGemini` | default |
| Simple Memory | `@n8n/n8n-nodes-langchain.memoryBufferWindow` | default |
| Get Inventory | `n8n-nodes-base.googleSheetsTool` | default |
| Get FAQ | `n8n-nodes-base.googleSheetsTool` | default |
| Post Orders | `n8n-nodes-base.googleSheetsTool` | default |
| Send message | `n8n-nodes-base.whatsApp` | send |

## Source

Prepared from the owner-supplied export `Whatsapp API Integration.json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
