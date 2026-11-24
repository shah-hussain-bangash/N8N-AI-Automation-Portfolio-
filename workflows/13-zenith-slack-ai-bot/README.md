# Zenith Slack AI Bot

Slack app mentions feed a Gemini assistant with memory; channel metadata is merged with the generated response and sent back to Slack.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `Slack Trigger`

Integrations: Slack, Google Gemini.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- Configure Slack event subscriptions and bot permissions, then test event payload and reply channel mappings.
- The memory key includes an event timestamp, which creates separate sessions per event. Use a deliberate conversation/thread key if multi-turn memory is required.
- The prompt asks for workspace file finding, but no search tool is connected. Do not present unsupported retrieval as an implemented capability.
- Review the organization-specific persona and personal endorsement in the source prompt before broader use.
- Verify mention filtering, bot-loop prevention and reply threading using a private test channel.

## Validation

8 nodes and 8 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| Slack Trigger | `n8n-nodes-base.slackTrigger` | default |
| AI Agent | `@n8n/n8n-nodes-langchain.agent` | default |
| Google Gemini Chat Model1 | `@n8n/n8n-nodes-langchain.lmChatGoogleGemini` | default |
| Simple Memory | `@n8n/n8n-nodes-langchain.memoryBufferWindow` | default |
| Merge | `n8n-nodes-base.merge` | default |
| Get Channel ID | `n8n-nodes-base.set` | default |
| Get Text | `n8n-nodes-base.set` | default |
| Send a message2 | `n8n-nodes-base.slack` | default |

## Source

Prepared from the owner-supplied export `Zenith AI Bot.json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
