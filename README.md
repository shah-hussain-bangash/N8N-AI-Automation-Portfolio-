# n8n AI Automation

A sequenced collection of AI-assisted lead operations, customer response workflows, WhatsApp campaigns, video generation, WordPress/Elementor building and social publishing, conversational agents and analytics collection. Each project includes a public workflow export, integration inventory, configuration guide and static validation report.

## Projects

| Order | Project | Workflow | Nodes |
| --- | --- | --- | --- |
| 01 | [AI Real Estate Lead Management](workflows/01-ai-real-estate-lead-management/README.md) | [JSON](workflows/01-ai-real-estate-lead-management/workflow.json) | 37 |
| 02 | [Lead Management, Outreach and Reporting](workflows/02-lead-management-and-reporting/README.md) | [JSON](workflows/02-lead-management-and-reporting/workflow.json) | 48 |
| 03 | [AI Email Reply Management](workflows/03-email-reply-management/README.md) | [JSON](workflows/03-email-reply-management/workflow.json) | 26 |
| 04 | [WhatsApp Template Campaigns](workflows/04-whatsapp-template-campaigns/README.md) | [JSON](workflows/04-whatsapp-template-campaigns/workflow.json) | 24 |
| 05 | [AI Video Generation and Delivery](workflows/05-ai-video-generation/README.md) | [JSON](workflows/05-ai-video-generation/workflow.json) | 27 |
| 06 | [Google Sheets Lead CRM](workflows/06-google-sheets-lead-crm/README.md) | [JSON](workflows/06-google-sheets-lead-crm/workflow.json) | 42 |
| 07 | [Real Estate Lead Agent](workflows/07-real-estate-lead-agent/README.md) | [JSON](workflows/07-real-estate-lead-agent/workflow.json) | 21 |
| 08 | [WordPress Elementor Subworkflow](workflows/08-wordpress-elementor-subworkflow/README.md) | [JSON](workflows/08-wordpress-elementor-subworkflow/workflow.json) | 5 |
| 09 | [Elementor Chat Agent](workflows/09-elementor-chat-agent/README.md) | [JSON](workflows/09-elementor-chat-agent/workflow.json) | 6 |
| 10 | [AI Post Generator and Publisher](workflows/10-ai-post-generator-publisher/README.md) | [JSON](workflows/10-ai-post-generator-publisher/workflow.json) | 19 |
| 11 | [WhatsApp Customer Service Agent](workflows/11-whatsapp-customer-service-agent/README.md) | [JSON](workflows/11-whatsapp-customer-service-agent/workflow.json) | 8 |
| 12 | [Facebook Leads to Odoo CRM](workflows/12-facebook-leads-to-odoo/README.md) | [JSON](workflows/12-facebook-leads-to-odoo/workflow.json) | 11 |
| 13 | [Zenith Slack AI Bot](workflows/13-zenith-slack-ai-bot/README.md) | [JSON](workflows/13-zenith-slack-ai-bot/workflow.json) | 8 |
| 14 | [GA4 Daily Collector](workflows/14-ga4-daily-collector/README.md) | [JSON](workflows/14-ga4-daily-collector/workflow.json) | 7 |
| 15 | [GSC Daily Collector](workflows/15-gsc-daily-collector/README.md) | [JSON](workflows/15-gsc-daily-collector/workflow.json) | 7 |

The sequence moves from lead intake and orchestration to reply handling, campaign delivery and media generation. These fifteen workflows are independent exports; numbering does not imply automatic cross-workflow execution.

## Getting started

Open a project README, import its workflow JSON into n8n, configure the listed credentials/resources and resolve its review items. Start with synthetic data in a test environment. Exports are inactive and contain configuration placeholders.

## Publication status

All fifteen exports were checked for valid JSON, unique node names/IDs and valid connection targets. Account references and hardcoded contact values were removed from public copies; originals were not modified. These checks do not replace an n8n import or live integration test. Known incomplete mappings and logic assumptions are documented per project.

No live workflow was run, and no email, WhatsApp message or call was sent during publication. This catalog covers the fifteen supplied exports; it does not claim the earlier archive collections have been uploaded.

## Repository layout

```text
workflows/
  01-ai-real-estate-lead-management/
  02-lead-management-and-reporting/
  03-email-reply-management/
  04-whatsapp-template-campaigns/
  05-ai-video-generation/
  06-google-sheets-lead-crm/
  07-real-estate-lead-agent/
  08-wordpress-elementor-subworkflow/
  09-elementor-chat-agent/
  10-ai-post-generator-publisher/
  11-whatsapp-customer-service-agent/
  12-facebook-leads-to-odoo/
  13-zenith-slack-ai-bot/
  14-ga4-daily-collector/
  15-gsc-daily-collector/
    README.md
    CONFIGURATION.md
    workflow.json
    validation.json
```

Each project directory contains the same four files. Attribution and existing public template references remain with their respective workflows.
