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
| 16 | [Website Uptime Monitor](workflows/16-uptime-monitor/README.md) | [JSON](workflows/16-uptime-monitor/workflow.json) | 7 |
| 17 | [PageSpeed Performance Monitor](workflows/17-pagespeed-monitor/README.md) | [JSON](workflows/17-pagespeed-monitor/workflow.json) | 7 |
| 18 | [Keyword Ranking Collector](workflows/18-keyword-ranking/README.md) | [JSON](workflows/18-keyword-ranking/workflow.json) | 7 |
| 19 | [Master Traffic Orchestrator](workflows/19-master-traffic-orchestrator/README.md) | [JSON](workflows/19-master-traffic-orchestrator/workflow.json) | 13 |
| 20 | [EspoCRM Lead Management](workflows/20-espocrm-lead-management/README.md) | [JSON](workflows/20-espocrm-lead-management/workflow.json) | 34 |
| 21 | [EspoCRM Email Reply Management](workflows/21-espocrm-email-reply-management/README.md) | [JSON](workflows/21-espocrm-email-reply-management/workflow.json) | 50 |
| 22 | [Social Media Post Automation](workflows/22-social-media-post-automation/README.md) | [JSON](workflows/22-social-media-post-automation/workflow.json) | 36 |
| 23 | [AI Outbound Call Agent](workflows/23-ai-outbound-call-agent/README.md) | [JSON](workflows/23-ai-outbound-call-agent/workflow.json) | 8 |
| 24 | [Multi-site Traffic Monitoring](workflows/24-multi-site-traffic-monitoring/README.md) | [JSON](workflows/24-multi-site-traffic-monitoring/workflow.json) | 85 |

The sequence moves from lead intake and orchestration to reply handling, campaign delivery and media generation. These 24 projects are supplied exports; numbering does not configure n8n workflow IDs. Project 19 calls collectors 14–18 after their destinations are selected during setup.

## Getting started

Open a project README, import its workflow JSON into n8n, configure the listed credentials/resources and resolve its review items. Start with synthetic data in a test environment. Exports are inactive and contain configuration placeholders.

## Publication status

All 24 exports were checked for valid JSON, unique node names/IDs and valid connection targets. Account references and hardcoded contact values were removed from public copies; originals were not modified. These checks do not replace an n8n import or live integration test. Known incomplete mappings and logic assumptions are documented per project.

No live workflow was run, and no email, WhatsApp message or call was sent during publication. This catalog covers the 24 supplied exports; it does not claim the earlier archive collections have been uploaded.

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
  16-uptime-monitor/
  17-pagespeed-monitor/
  18-keyword-ranking/
  19-master-traffic-orchestrator/
  20-espocrm-lead-management/
  21-espocrm-email-reply-management/
  22-social-media-post-automation/
  23-ai-outbound-call-agent/
  24-multi-site-traffic-monitoring/
    README.md
    CONFIGURATION.md
    workflow.json
    validation.json
```

Each project directory contains the same four files. Attribution and existing public template references remain with their respective workflows.

## Traffic monitoring suite

Import and configure [collectors 14–18 and master orchestrator 19](workflows/19-master-traffic-orchestrator/README.md#collector-import-and-mapping-order) using the destination mapping guide. Reassign all subworkflow IDs after import. [Project 24](workflows/24-multi-site-traffic-monitoring/README.md) is a separate multi-site reporting export; its source filename does not establish that 320 sites have been load-tested.
