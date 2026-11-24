# Configuration

Original account values are not included. Configure the resources in these nodes after import. Numbered placeholders distinguish original resource values; use the same replacement wherever a placeholder repeats. Do not treat placeholders as usable credentials.

| Node | Public placeholder |
| --- | --- |
| Page_Performance | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_1` |
| Daily_Summary | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_2` |
| Weekly_Summary | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_3` |
| Monthly_Summary | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_4` |
| Query_Performance | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_5` |
| Fetch GA4 Daily Traffic | `REPLACE_WITH_GA4_PROPERTY_1` |
| Clean GA4 Daily Traffic | `REPLACE_WITH_GA4_PROPERTY_1` |
| GA4 Daily Summary | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_6` |
| GA4 Weekly Summary | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_7` |
| GA4 Monthly Summary | `REPLACE_WITH_DOCUMENTID_1`, `REPLACE_WITH_SHEETNAME_8` |
| Select Preferred GA4 Properties | `REPLACE_WITH_GA4_PROPERTY_1`, `REPLACE_WITH_GA4_PROPERTY_2`, `REPLACE_WITH_GA4_PROPERTY_3` |
| HTTP Request — Slack | `REPLACE_WITH_SLACK_DESTINATION_1` |

## Credential types present in the source

`googleOAuth2Api`, `googleSheetsOAuth2Api`, `slackApi`

This is an inventory of exported credential types, not an exhaustive list of required connections. Nodes with empty configuration may require additional credentials.

## Existing source placeholders

No legacy placeholder markers detected.

## Google Sheets mapped columns

`averagePosition`, `clicks`, `ctrPercent`, `dataStatus`, `date`, `domain`, `engagedSessions`, `impressions`, `newUsers`, `pagePath`, `pageUrl`, `periodEnd`, `periodStart`, `permissionLevel`, `propertyId`, `query`, `recordKey`, `sessions`, `views`, `visitors`, `website`

## Public-export preparation

Workflow activation disabled; exported account credential references, cached resource labels/links and deployment metadata removed; hardcoded contact and resource values replaced. Source files remain unchanged. Existing node logic, layout and connections are retained.
