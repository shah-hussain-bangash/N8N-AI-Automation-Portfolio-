# Configuration

Original account values are not included. Configure the resources in these nodes after import. Numbered placeholders distinguish original resource values; use the same replacement wherever a placeholder repeats. Do not treat placeholders as usable credentials.

| Node | Public placeholder |
| --- | --- |
| Google Sheets Get Row(s) | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Google Sheets Update Row | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Update Lead Status (Interested) | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Slack Notification (Customer Interested) | `REPLACE_WITH_CHANNELID_1` |
| Create Call Task (Interested) | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Update Lead Status (Meeting Requested) | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Create Calendar Event (Meeting) | `REPLACE_WITH_CALENDAR_1` |
| Slack Notification (Meeting Requested) | `REPLACE_WITH_CHANNELID_1` |
| Update Lead Status (Question) | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Slack Notification (Question Received) | `REPLACE_WITH_CHANNELID_1` |
| Update Lead Status (Lost) | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Slack Notification (Not Interested) | `REPLACE_WITH_CHANNELID_1` |
| Update Lead Status (Callback Needed) | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Create Call Task (Priority High) | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Slack Notification (Callback Needed) | `REPLACE_WITH_CHANNELID_2` |
| Append to Audit Log | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_2` |
| Notify Sales Team | `REPLACE_WITH_CHANNELID_1` |
| Slack Alert - Lead Not Found | `REPLACE_WITH_CHANNELID_3` |

## Credential types present in the source

`googleCalendarOAuth2Api`, `googleSheetsOAuth2Api`, `imap`, `openAiApi`, `slackApi`

This is an inventory of exported credential types, not an exhaustive list of required connections. Nodes with empty configuration may require additional credentials.

## Existing source placeholders

No legacy placeholder markers detected.

## Google Sheets mapped columns

` Audit ID`, `AI Confidence`, `AI Intent`, `AI Priority`, `AI Summary`, `Action`, `Approval Status`, `Assigned Sales Person`, `Call Completed`, `Channel`, `Created At`, `Customer Reply`, `Date`, `Details`, `Email`, `Follow-up Date`, `Last Contact Method`, `Last Reply Date`, `Last Updated`, `Lead ID`, `Lead Status`, `Message ID`, `New Status`, `Notes`, `Performed By`, `Previous Status`, `Priority`, `Recommended Action`, `Remarks`, `Reply Received`, `Sentiment`, `Status`, `Task Type`, `Time`, `User`

## Public-export preparation

Workflow activation disabled; exported account credential references, cached resource labels/links and deployment metadata removed; hardcoded contact and resource values replaced. Source files remain unchanged. Existing node logic, layout and connections are retained.
