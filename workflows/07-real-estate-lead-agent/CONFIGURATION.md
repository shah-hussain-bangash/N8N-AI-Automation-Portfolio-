# Configuration

Original account values are not included. Configure the resources in these nodes after import. Numbered placeholders distinguish original resource values; use the same replacement wherever a placeholder repeats. Do not treat placeholders as usable credentials.

| Node | Public placeholder |
| --- | --- |
| Classification Model | `REPLACE_WITH_MODEL_1` |
| Draft Model | `REPLACE_WITH_MODEL_1` |
| Slack Lead Summary | `REPLACE_WITH_CHANNELID_1` |
| Human Approval | `REPLACE_WITH_CHANNELID_2` |
| Send Brevo Email | `REPLACE_WITH_EMAIL_1` |
| Return to Sales Team | `REPLACE_WITH_CHANNELID_3` |

## Credential types present in the source

`openAiApi`, `sendInBlueApi`, `slackApi`

This is an inventory of exported credential types, not an exhaustive list of required connections. Nodes with empty configuration may require additional credentials.

## Existing source placeholders

- Power BI Push
- Send Brevo Email
- Send WhatsApp

## Google Sheets mapped columns

No explicit column mappings exported.

## Public-export preparation

Workflow activation disabled; exported account credential references, cached resource labels/links and deployment metadata removed; hardcoded contact and resource values replaced. Source files remain unchanged. Existing node logic, layout and connections are retained.
