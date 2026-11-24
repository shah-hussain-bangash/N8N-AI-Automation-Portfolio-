# n8n AI Automation Portfolio

Business automations and system integrations built with n8n. This portfolio is being prepared for publication. Workflow exports and demo evidence will be added as they are ready to share.

## Workflow catalog

Each published workflow will have its own directory under `workflows/`. The catalog will link to the workflow, describe the business outcome, and point to the available test evidence.

## Where to put a workflow

Use `workflows/<workflow-name>/` for each automation and keep its supporting files together.

| File | What it contains |
| --- | --- |
| `workflow.json` | An importable n8n workflow export with sensitive values removed |
| `README.md` | The business problem, trigger, integrations, setup, and expected output |
| `sample-input.json` | Synthetic input for a reproducible demo, where applicable |
| `evidence/` | Approved screenshots, run results, or a short demo showing success and recovery |

For each workflow, identify what you built and show a normal run plus one relevant failure case, such as a duplicate submission or an unavailable API.

[Back to the GitHub portfolio](https://github.com/shah-hussain-bangash)
