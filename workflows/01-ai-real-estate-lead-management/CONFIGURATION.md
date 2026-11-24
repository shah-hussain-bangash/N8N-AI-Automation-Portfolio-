# Configuration

Original account values are not included. Configure the resources in these nodes after import. Numbered placeholders distinguish original resource values; use the same replacement wherever a placeholder repeats. Do not treat placeholders as usable credentials.

| Node | Public placeholder |
| --- | --- |
| Send WhatsApp (Approved Template) | `REPLACE_WITH_PHONENUMBERID_1` |
| Attach Follow-up Activity in Odoo | `REPLACE_WITH_RES_MODEL_1` |
| Send Follow-up WhatsApp (If No Response) | `REPLACE_WITH_PHONENUMBERID_1` |

## Credential types present in the source

`openAiApi`, `sendInBlueApi`, `slackOAuth2Api`, `whatsAppApi`

This is an inventory of exported credential types, not an exhaustive list of required connections. Nodes with empty configuration may require additional credentials.

## Existing source placeholders

- Attach Brochure / Project Details
- Send Brevo Email (Approved Template)
- Send Data to Power BI
- Send Follow-up Email (If No Response)

## Google Sheets mapped columns

No explicit column mappings exported.

## Public-export preparation

Workflow activation disabled; exported account credential references, cached resource labels/links and deployment metadata removed; hardcoded contact and resource values replaced. Source files remain unchanged. Existing node logic, layout and connections are retained.
