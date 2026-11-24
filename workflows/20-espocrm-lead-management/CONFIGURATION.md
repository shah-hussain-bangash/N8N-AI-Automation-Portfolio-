# Configuration

Original account values are not included. Configure the resources in these nodes after import. Numbered placeholders distinguish original resource values; use the same replacement wherever a placeholder repeats. Do not treat placeholders as usable credentials.

| Node | Public placeholder |
| --- | --- |
| Send Error Alert (Slack) | `REPLACE_WITH_CHANNELID_1` |
| Post Lead Summary (Slack) | `REPLACE_WITH_CHANNELID_1` |
| Sales Manager Approval | `REPLACE_WITH_CHANNELID_1` |
| Return to Sales Team (Slack) | `REPLACE_WITH_CHANNELID_1` |
| Notify Sales Team (Rejected) | `REPLACE_WITH_CHANNELID_1` |
| Send Email (Brevo) | `REPLACE_WITH_EMAIL_1` |
| Send WhatsApp | `REPLACE_WITH_PHONENUMBERID_1` |
| Search Existing Lead - EspoCRM | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Create New Lead - EspoCRM | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Update Existing Lead - EspoCRM | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| EspoCRM Update Lead | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Create EspoCRM Activity Log | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Search Opportunity - EspoCRM | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| EspoCRM Update Lead1 | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST`, `REPLACE_WITH_LEAD_RECORD_ID` |
| Create Opportunity - EspoCRM | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Link Opportunity to Lead | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Update Existing Opportunity - EspoCRM | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |

## Credential types present in the source

`openAiApi`, `sendInBlueApi`, `slackApi`, `whatsAppApi`

This is an inventory of exported credential types, not an exhaustive list of required connections. Nodes with empty configuration may require additional credentials.

## Existing source placeholders

No legacy placeholder markers detected.

## Google Sheets mapped columns

No explicit column mappings exported.

## Public-export preparation

Workflow activation disabled; exported account credential references, cached resource labels/links and deployment metadata removed; hardcoded contact and resource values replaced. Source files remain unchanged. Existing node logic, layout and connections are retained.
