# Configuration

Original account values are not included. Configure the resources in these nodes after import. Numbered placeholders distinguish original resource values; use the same replacement wherever a placeholder repeats. Do not treat placeholders as usable credentials.

| Node | Public placeholder |
| --- | --- |
| Get row(s) in sheet | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Create a post | `REPLACE_WITH_PERSON_1` |
| Update row in sheet | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Send message and wait for response | `REPLACE_WITH_CHATID_1` |
| Send a photo message | `REPLACE_WITH_CHATID_1` |
| Search files and folders | `REPLACE_WITH_FOLDERID_1` |
| Get row(s) in sheet1 | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Create a post1 | `REPLACE_WITH_PERSON_1` |
| Update row in sheet1 | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |

## Credential types present in the source

`anthropicApi`, `googleDriveOAuth2Api`, `googleSheetsOAuth2Api`, `linkedInOAuth2Api`, `telegramApi`

This is an inventory of exported credential types, not an exhaustive list of required connections. Nodes with empty configuration may require additional credentials.

## Existing source placeholders

No legacy placeholder markers detected.

## Google Sheets mapped columns

`Category`, `Generated Post`, `ID`, `LinkedIn URL`, `Publish Date`, `Status`, `Topic`

## Public-export preparation

Workflow activation disabled; exported account credential references, cached resource labels/links and deployment metadata removed; hardcoded contact and resource values replaced. Source files remain unchanged. Existing node logic, layout and connections are retained.
