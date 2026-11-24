# Elementor Chat Agent

Chat-triggered Anthropic agent with image uploads, screenshot-to-Elementor instructions and an n8n workflow tool, intended to delegate website-building actions to a configured workflow.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `When chat message received`

Integrations: Anthropic, n8n Workflow Tool.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- Call n8n Workflow Tool has no configured target workflow or input mappings. Select and map an imported builder workflow explicitly; numbering does not connect them.
- Basic LLM Chain and its model branch are disconnected from the active chat path. Configure or remove them deliberately.
- The system prompt targets a specific test site and page, replaced here with placeholders. Set a staging destination and enforce its draft-only restrictions in the called workflow as well.
- Verify uploaded-image handling and tool-input validation against the chosen Anthropic model and destination workflow.

## Validation

6 nodes and 3 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| When chat message received | `@n8n/n8n-nodes-langchain.chatTrigger` | default |
| Basic LLM Chain | `@n8n/n8n-nodes-langchain.chainLlm` | default |
| Anthropic Chat Model | `@n8n/n8n-nodes-langchain.lmChatAnthropic` | default |
| AI Agent | `@n8n/n8n-nodes-langchain.agent` | default |
| Anthropic Chat Model1 | `@n8n/n8n-nodes-langchain.lmChatAnthropic` | default |
| Call n8n Workflow Tool | `@n8n/n8n-nodes-langchain.toolWorkflow` | default |

## Source

Prepared from the owner-supplied export `Elementor Website Builder.json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
