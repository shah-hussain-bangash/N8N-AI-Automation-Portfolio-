# Configuration

Original account values are not included. Configure the resources in these nodes after import. Numbered placeholders distinguish original resource values; use the same replacement wherever a placeholder repeats. Do not treat placeholders as usable credentials.

| Node | Public placeholder |
| --- | --- |
| Send Error Alert (Slack) | `REPLACE_WITH_CHANNELID_1` |
| Search Existing Lead | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Update Existing Lead | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Create New Lead | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| AI Generate Draft | `REPLACE_WITH_EMAIL_1`, `REPLACE_WITH_PHONE_1` |
| Post Lead Summary (Slack) | `REPLACE_WITH_CHANNELID_1` |
| Sales Manager Approval | `REPLACE_WITH_CHANNELID_1` |
| Return to Sales Team (Slack) | `REPLACE_WITH_CHANNELID_1` |
| Notify Sales Team (Rejected) | `REPLACE_WITH_CHANNELID_1` |
| Send Email (Brevo) | `REPLACE_WITH_EMAIL_2` |
| Send WhatsApp | `REPLACE_WITH_PHONENUMBERID_1` |
| Update Google Sheets (Contacted) | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Log & Audit Trail | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_2` |
| Check Response Status | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Update Status (Interested/Meeting) | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Send Reminder WhatsApp | `REPLACE_WITH_PHONENUMBERID_1` |
| Create Call Task (in Sheet) | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Notify Sales Team (Follow-up) | `REPLACE_WITH_USER_1` |
| New Lead Found | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_3` |
| Start AI Call (ElevenLabs + Twilio) | `REPLACE_WITH_PROVIDER_ID_1`, `REPLACE_WITH_PROVIDER_ID_2`, `REPLACE_WITH_PROVIDER_ID_3` |
| Update Lead Row | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_3` |
| Slack Notification (Customer Interested) | `REPLACE_WITH_CHANNELID_1` |

## Credential types present in the source

`googleSheetsOAuth2Api`, `googleSheetsTriggerOAuth2Api`, `httpHeaderAuth`, `openAiApi`, `sendInBlueApi`, `slackApi`, `whatsAppApi`

This is an inventory of exported credential types, not an exhaustive list of required connections. Nodes with empty configuration may require additional credentials.

## Existing source placeholders

- Send Reminder Email

## Google Sheets mapped columns

` Audit ID`, `AI Lead Score`, `AI Lead Type`, `AI Priority`, `Action`, `Approval Status`, `Area Preference`, `Assigned Sales Person`, `Assigned Team`, `AssignedSalesPerson`, `Budget`, `Call Completed`, `Call Duration`, `Call Outcome`, `Call SID`, `Call Sentiment`, `Call Status`, `Call Summary`, `Call Summary Title`, `Campaign`, `Channel`, `Conversation ID`, `CreatedDate`, `Date`, `Details`, `Email`, `Email Sent`, `Follow-up Date`, `Investment Type`, `Language`, `Last Call Date`, `Last Updated`, `Lead`, `Lead Date`, `Lead ID`, `Lead Status`, `Lead Time`, `Message`, `Mobile`, `Name`, `New Status`, `Performed By`, `Phone`, `Platform`, `Previous Status`, `Property Type`, `ROI Interest`, `Remarks`, `Sentiment`, `Source`, `Status`, `Task`, `Time`, `User`, `Website`, `WhatsApp Sent`, `row_number`

## Public-export preparation

Workflow activation disabled; exported account credential references, cached resource labels/links and deployment metadata removed; hardcoded contact and resource values replaced. Source files remain unchanged. Existing node logic, layout and connections are retained.
