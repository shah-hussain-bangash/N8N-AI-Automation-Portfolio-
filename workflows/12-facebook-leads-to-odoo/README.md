# Facebook Leads to Odoo CRM

Facebook Lead Ads intake, rule-based segmentation and scoring, Odoo duplicate checks and opportunity creation, welcome WhatsApp/email messages and Slack notifications.

**Status:** Sanitized workflow export for configuration and review. Inactive by default. Runtime behavior has not been verified in this publication process.

## Architecture

Entry points: `New Facebook Lead`

Integrations: Facebook Lead Ads, Odoo CRM, WhatsApp Business, Gmail, Slack.

## Setup

1. Import [workflow.json](workflow.json) into a compatible n8n installation. Verify that every node type and exported node version is supported.
2. Create the service credentials and replace all values listed in [CONFIGURATION.md](CONFIGURATION.md), including any existing source placeholders.
3. Configure destination resources, expected field names, template mappings and access scopes. Use isolated test accounts and synthetic data.
4. Resolve the review items below, then manually test success, rejection, missing-data and provider-failure paths. Inspect delivery/audit results before activation.

## Review before activation

- Select the Facebook page and form, configure Odoo and messaging credentials, and select notification channels.
- Test the no-match result of Find Existing Lead. If the node returns zero items, enable appropriate empty-result handling so new leads can reach creation.
- Segment desk IDs are all zero and the Odoo create mapping does not set user_id. Real salesperson assignment requires explicit mapping; a desk name in a description is not CRM assignment.
- Validate required contact fields and form mappings before duplicate detection or outreach; qualification is deterministic rules, not an LLM model.
- Verify consent, template requirements and test destinations before enabling welcome messages.

## Validation

11 nodes and 8 connections inspected. JSON parsing, unique node names/IDs and connection targets checked. See [validation.json](validation.json). Static checks do not establish expression correctness, API compatibility, delivery success or production readiness. No service was contacted and no messages or calls were sent.

## Node inventory

| Node | Type | Exported operation |
| --- | --- | --- |
| New Facebook Lead | `n8n-nodes-base.facebookLeadAdsTrigger` | default |
| Normalize & Qualify | `n8n-nodes-base.code` | default |
| Find Existing Lead | `n8n-nodes-base.odoo` | default |
| Is Duplicate? | `n8n-nodes-base.if` | default |
| Notify Duplicate | `n8n-nodes-base.slack` | default |
| Create Odoo Opportunity | `n8n-nodes-base.odoo` | create |
| Welcome WhatsApp | `n8n-nodes-base.whatsApp` | send |
| Welcome Email | `n8n-nodes-base.gmail` | default |
| Notify Assigned Agent | `n8n-nodes-base.slack` | default |

## Source

Prepared from the owner-supplied export `Real Estate Lead Pipeline → Odoo CRM.json`. Existing in-workflow attribution and public reference links are retained where present; no sole-authorship claim is made for third-party templates or nodes. No production performance metrics or screenshots are claimed.
