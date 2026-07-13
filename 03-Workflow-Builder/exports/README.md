# Workflow Builder Exports

This folder contains exported Docusign Workflow Builder files (`.json`) that can be imported directly into your sandbox.

## Available Exports

| File | Description | Trigger Type |
|------|-------------|--------------|
| `vendor-onboarding-nda.json` | Vendor NDA workflow with conditional signed/declined routing | Web Form |
| `employee-onboarding-packet.json` | Multi-document employee onboarding with sequential signing | API / Scheduled |
| `procurement-approval.json` | Procurement approval workflow with manager escalation step | Web Form |

## How to Import

1. Log in to your Docusign sandbox
2. Navigate to **Agreements > Workflow Builder**
3. Click the **Import** button (top right)
4. Select the `.json` file you want to import
5. Review the imported workflow — check participant mappings and template references
6. Update any template IDs to match templates in your own sandbox
7. Click **Publish** when ready to activate

## How to Export Your Own Workflows

1. Open any workflow in Workflow Builder
2. Click the **...** menu (top right)
3. Select **Export**
4. Save the `.json` file and add it to this folder

## Notes

- Exported workflows reference template IDs from the original account. You must re-link templates after importing into a different account.
- Webhook URLs in exported workflows must be updated to point to your own endpoints.
