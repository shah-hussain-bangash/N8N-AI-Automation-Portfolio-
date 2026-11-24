# Configuration

Original account values are not included. Configure the resources in these nodes after import. Numbered placeholders distinguish original resource values; use the same replacement wherever a placeholder repeats. Do not treat placeholders as usable credentials.

| Node | Public placeholder |
| --- | --- |
| Search Lead - EspoCRM | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Save Customer Reply - EspoCRM | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Create Customer Reply Activity - EspoCRM | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Update AI Analysis - EspoCRM | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Update Lead - Interested | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| EspoCRM Activity - Interested | `REPLACE_WITH_ESPOCRM_HOST` |
| Create EspoCRM Follow-up Task | `REPLACE_WITH_ESPOCRM_HOST` |
| Update Lead - Meeting Requested | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Create Google Calendar Event | `REPLACE_WITH_CALENDAR_1` |
| Create EspoCRM Meeting Activity | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Slack Notification - Meeting Scheduled | `REPLACE_WITH_CHANNELID_1` |
| Create EspoCRM Meeting Activity (No Date) | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Slack Notification - Meeting (Confirm Time) | `REPLACE_WITH_CHANNELID_1` |
| Update Lead - Follow-up Required | `REPLACE_WITH_ESPOCRM_HOST` |
| EspoCRM Activity - Question | `REPLACE_WITH_ESPOCRM_HOST` |
| Update Lead - Callback Requested | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Create EspoCRM Call Task | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Slack Notification - Callback Requested | `REPLACE_WITH_CHANNELID_1` |
| Update Lead - Lost | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| EspoCRM Activity - Lost | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Update Lead - General Reply | `REPLACE_WITH_ESPOCRM_HOST` |
| EspoCRM Activity - General Reply | `REPLACE_WITH_ESPOCRM_HOST` |
| Update Lead - Not Interested | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| EspoCRM Activity - Not Interested | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Slack Notification - Not Interested | `REPLACE_WITH_CHANNELID_1` |
| Slack Notification - Lost | `REPLACE_WITH_CHANNELID_1` |
| Update Lead - Unified | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Slack Notification - Callback Requested1 | `REPLACE_WITH_CHANNELID_1` |
| Slack Notification - General Reply | `REPLACE_WITH_CHANNELID_1` |
| Slack Notification - Meeting (Confirm Time)1 | `REPLACE_WITH_CHANNELID_1` |
| Create Google Calendar Event1 | `REPLACE_WITH_CALENDAR_1` |
| Create EspoCRM Meeting Activity1 | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Slack Notification - Meeting Scheduled1 | `REPLACE_WITH_CHANNELID_1` |
| Get Lead for Opportunity | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |
| Update Opportunity from Reply | `REPLACE_WITH_API_KEY_1`, `REPLACE_WITH_ESPOCRM_HOST` |

## Credential types present in the source

`googleCalendarOAuth2Api`, `imap`, `openAiApi`, `slackApi`

This is an inventory of exported credential types, not an exhaustive list of required connections. Nodes with empty configuration may require additional credentials.

## Existing source placeholders

No legacy placeholder markers detected.

## Google Sheets mapped columns

No explicit column mappings exported.

## Public-export preparation

Workflow activation disabled; exported account credential references, cached resource labels/links and deployment metadata removed; hardcoded contact and resource values replaced. Source files remain unchanged. Existing node logic, layout and connections are retained.
