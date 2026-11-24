# Configuration

Original account values are not included. Configure the resources in these nodes after import. Numbered placeholders distinguish original resource values; use the same replacement wherever a placeholder repeats. Do not treat placeholders as usable credentials.

| Node | Public placeholder |
| --- | --- |
| WF-02 GA4 Daily | `REPLACE_WITH_WORKFLOWID_1` |
| WF-04 GSC Daily | `REPLACE_WITH_WORKFLOWID_2` |
| WF-06 Uptime | `REPLACE_WITH_WORKFLOWID_3` |
| WF-07 PageSpeed | `REPLACE_WITH_WORKFLOWID_4` |
| WF-08 Keyword | `REPLACE_WITH_WORKFLOWID_5` |

## Credential types present in the source

`googleSheetsOAuth2Api`, `slackApi`

This is an inventory of exported credential types, not an exhaustive list of required connections. Nodes with empty configuration may require additional credentials.

## Existing source placeholders

No legacy placeholder markers detected.

## Google Sheets mapped columns

`Errors_Count`, `Run_At`, `Status`, `Websites_Processed`

## Public-export preparation

Workflow activation disabled; exported account credential references, cached resource labels/links and deployment metadata removed; hardcoded contact and resource values replaced. Source files remain unchanged. Existing node logic, layout and connections are retained.
