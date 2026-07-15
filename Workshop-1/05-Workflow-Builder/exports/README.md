# Workflow Builder Exports

This folder contains exported Docusign Workflow Builder files (`.json`) that can be imported directly into your sandbox.

## Available Exports

| File | Description | Trigger Type |
|------|-------------|--------------|
| `workflow-1-name.zip` | Workflow to receive inputs Claude LLM and send as a request to Agreement Desk | API |
| `workflow-2-name.zip` | Workflow to pull all the submitted requests in Agreement Desk, add documents, send approvals, and send envelopes for eSign | Events |

## How to Import

1. Log in to your Docusign Developer Account
2. Go to **Agreements > Workflows**
3. Select **Create Workflow**
4. Select **Import Workflow**.
5. Review the imported workflow — check participant mappings and template references
6. Update any template IDs to match templates in your own Developer account.
7. Select  **Save and Publish** when ready to activate

