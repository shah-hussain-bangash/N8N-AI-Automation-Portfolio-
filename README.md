# n8n AI Automation

A sequenced collection of AI-assisted lead operations, customer response workflows, WhatsApp campaigns and video generation. Each project includes a public workflow export, integration inventory, configuration guide and static validation report.

## Projects

| Order | Project | Workflow | Nodes |
| --- | --- | --- | --- |
| 01 | [AI Real Estate Lead Management](workflows/01-ai-real-estate-lead-management/README.md) | [JSON](workflows/01-ai-real-estate-lead-management/workflow.json) | 37 |
| 02 | [Lead Management, Outreach and Reporting](workflows/02-lead-management-and-reporting/README.md) | [JSON](workflows/02-lead-management-and-reporting/workflow.json) | 48 |
| 03 | [AI Email Reply Management](workflows/03-email-reply-management/README.md) | [JSON](workflows/03-email-reply-management/workflow.json) | 26 |
| 04 | [WhatsApp Template Campaigns](workflows/04-whatsapp-template-campaigns/README.md) | [JSON](workflows/04-whatsapp-template-campaigns/workflow.json) | 24 |
| 05 | [AI Video Generation and Delivery](workflows/05-ai-video-generation/README.md) | [JSON](workflows/05-ai-video-generation/workflow.json) | 27 |

The sequence moves from lead intake and orchestration to reply handling, campaign delivery and media generation. These five workflows are independent exports; numbering does not imply automatic cross-workflow execution.

## Getting started

Open a project README, import its workflow JSON into n8n, configure the listed credentials/resources and resolve its review items. Start with synthetic data in a test environment. Exports are inactive and contain configuration placeholders.

## Publication status

All five exports were checked for valid JSON, unique node names/IDs and valid connection targets. Account references and hardcoded contact values were removed from public copies; originals were not modified. These checks do not replace an n8n import or live integration test. Known incomplete mappings and logic assumptions are documented per project.

No live workflow was run, and no email, WhatsApp message or call was sent during publication. This catalog covers the five supplied exports; it does not claim the earlier archive collections have been uploaded.

## Repository layout

```text
workflows/
  01-ai-real-estate-lead-management/
  02-lead-management-and-reporting/
  03-email-reply-management/
  04-whatsapp-template-campaigns/
  05-ai-video-generation/
    README.md
    CONFIGURATION.md
    workflow.json
    validation.json
```

Each project directory contains the same four files. Attribution and existing public template references remain with their respective workflows.
