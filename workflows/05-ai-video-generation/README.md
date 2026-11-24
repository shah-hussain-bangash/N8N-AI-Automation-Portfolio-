# AI Video Generation and Delivery

Prompt form submission, RapidAPI Veo task creation and polling, video download, Google Drive upload and email notifications.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `On form submission`

Integrations: RapidAPI Veo provider, Google Drive, SMTP email.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- This export calls a third-party RapidAPI Veo endpoint. Verify provider availability, model version and request/response schema.
- Set Google Drive Permissions targets a fixed file and specifies owner/anyone. Replace with the newly uploaded file reference and an appropriate permission policy before enabling.
- Add polling deadlines, retry limits and failure handling for tasks that never finish.
- Review the upload binary field and email link mappings against actual provider responses.

## Validation

27 nodes and 13 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| On form submission | `n8n-nodes-base.formTrigger` | default |
| Wait for API Response | `n8n-nodes-base.wait` | default |
| API Request: Check Task Status | `n8n-nodes-base.httpRequest` | default |
| Condition: Task Output Status | `n8n-nodes-base.switch` | default |
| Wait for Task to Complete | `n8n-nodes-base.wait` | default |
| Send Email: API Error - Task ID Missing | `n8n-nodes-base.emailSend` | default |
| Upload File to Google Drive | `n8n-nodes-base.googleDrive` | default |
| Send Email: API Error - Task Failed | `n8n-nodes-base.emailSend` | default |
| Set Google Drive Permissions | `n8n-nodes-base.googleDrive` | share |
| Condition: Check Task Id | `n8n-nodes-base.if` | default |
| Veo 3 Fast API Processor | `n8n-nodes-base.httpRequest` | default |
| Send an email : Video Link | `n8n-nodes-base.emailSend` | default |
| Download Video | `n8n-nodes-base.httpRequest` | default |

## Source

Prepared from the owner-supplied export `Generate videos automatically with Veo3 Fast API, Google Drive & email notifications.json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
