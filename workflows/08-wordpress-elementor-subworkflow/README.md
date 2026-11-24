# WordPress Elementor Subworkflow

Callable workflow accepting page title, slug, status and Elementor layout data; tests WordPress authentication, creates a page and calls a custom layout-save endpoint.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `When Executed by Another Workflow`

Integrations: WordPress REST API, HTTP Basic authentication / WordPress application password, Custom Elementor save endpoint.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- Requires an existing custom /wp-json/zenith-n8n/v1/elementor/save server endpoint. Its plugin or implementation is not included in this export.
- Configure a staging WordPress site, restricted credentials and draft page status before testing; the workflow can create pages.
- The save request reads $json.id from the page-create response. Verify that response shape and Elementor layout schema.
- WordPress – Connection Test1 is a disconnected diagnostic node with a source page ID; choose an appropriate test page if using it.

## Validation

5 nodes and 3 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| When Executed by Another Workflow | `n8n-nodes-base.executeWorkflowTrigger` | default |
| WordPress – Connection Test | `n8n-nodes-base.httpRequest` | default |
| HTTP Request | `n8n-nodes-base.httpRequest` | default |
| WordPress – Connection Test1 | `n8n-nodes-base.httpRequest` | default |
| HTTP Request1 | `n8n-nodes-base.httpRequest` | default |

## Source

Prepared from the owner-supplied export `WordPress Elementor Builder.json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
