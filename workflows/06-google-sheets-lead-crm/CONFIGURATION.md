# Configuration

Original account values are not included. Configure the resources in these nodes after import. Numbered placeholders distinguish original resource values; use the same replacement wherever a placeholder repeats. Do not treat placeholders as usable credentials.

| Node | Public placeholder |
| --- | --- |
| Send Error Alert (Slack) | `REPLACE_WITH_CHANNELID_1` |
| Search Existing Lead | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Update Existing Lead | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Create New Lead | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Save AI Data to Google Sheets | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_2` |
| Post Lead Summary (Slack) | `REPLACE_WITH_CHANNELID_1` |
| Sales Manager Approval | `REPLACE_WITH_CHANNELID_1` |
| Return to Sales Team (Slack) | `REPLACE_WITH_CHANNELID_2` |
| Notify Sales Team (Rejected) | `REPLACE_WITH_CHANNELID_3` |
| Send Email (Brevo) | `REPLACE_WITH_EMAIL_1` |
| Send WhatsApp | `REPLACE_WITH_PHONENUMBERID_1` |
| Update Google Sheets (Contacted) | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Log & Audit Trail | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Check Response Status | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Update Status (Interested/Meeting) | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Send Reminder WhatsApp | `REPLACE_WITH_PHONENUMBERID_1` |
| Create Call Task (in Sheet) | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Notify Sales Team (Follow-up) | `REPLACE_WITH_USER_1` |
| Save AI Data to Google Sheets1 | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_2` |

## Credential types present in the source

`googleSheetsOAuth2Api`, `openAiApi`, `sendInBlueApi`, `slackApi`, `whatsAppApi`

This is an inventory of exported credential types, not an exhaustive list of required connections. Nodes with empty configuration may require additional credentials.

## Existing source placeholders

- Push Data to Power BI
- Send Reminder Email

## Google Sheets mapped columns

`AIReason`, `Approval Status`, `Area Preference`, `AreaPreference`, `Assigned Sales Person`, `Assigned Team`, `AssignedSalesPerson`, `Budget`, `Call Completed`, `ConfidenceScore`, `CreatedDate`, `Email`, `Email Sent`, `Follow-up Date`, `Investment Type`, `InvestmentInterest`, `Language`, `Last Updated`, `Lead`, `Lead Date`, `Lead ID`, `Lead Status`, `Lead Time`, `LeadScore`, `LeadType`, `Message`, `Mobile`, `Name`, `Phone`, `Priority`, `Property Type`, `ROI Interest`, `RecommendedSalesTeam`, `Sentiment`, `Task`, `Website`, `WhatsApp Sent`

## Public-export preparation

Workflow activation disabled; exported account credential references, cached resource labels/links and deployment metadata removed; hardcoded contact and resource values replaced. Source files remain unchanged. Existing node logic, layout and connections are retained.
