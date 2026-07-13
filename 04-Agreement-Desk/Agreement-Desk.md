# Agreement Desk

This module introduces **Agreement Desk** — Docusign's unified workspace for managing agreements across their full lifecycle.

---

## Overview

**Agreement Desk** gives teams a single place to:

- View all agreements in one dashboard (sent, pending, completed, expiring)
- Organize agreements by type, owner, or custom category
- Track key dates (expiration, renewal, effective date)
- Collaborate with internal stakeholders on agreement review
- Trigger actions like renewal reminders and re-sends

---

## Key Concepts

| Concept | Description |
|---------|-------------|
| **Agreement** | Any document tracked in Agreement Desk — envelopes, uploaded files, or imported contracts |
| **Lifecycle Stage** | Where the agreement is: Draft, In Review, Active, Expiring, Expired, Terminated |
| **Custom Fields** | Metadata fields you define to categorize and search agreements |
| **Party** | An internal or external person associated with an agreement |

---

## Lab Steps

### Step 1 — Access Agreement Desk

1. Log in to your Docusign sandbox
2. Navigate to **Agreements > Agreement Desk**
3. You will see the main dashboard with lifecycle-based columns

> Screenshot placeholder: `../assets/images/04-agreement-desk-dashboard.png`

---

### Step 2 — Import a Demo Agreement

Sample agreements for this lab are in the [`demo-agreements/`](./demo-agreements/) folder.

1. Click **+ New Agreement** in Agreement Desk
2. Select **Upload a file**
3. Upload `demo-agreements/vendor-nda-signed.pdf`
4. Fill in metadata:
   - Agreement Name: `Vendor NDA - Acme Corp`
   - Type: `NDA`
   - Effective Date: today's date
   - Expiration Date: 1 year from today
5. Click **Save**

---

### Step 3 — Configure Custom Fields

1. Navigate to **Settings > Agreement Desk > Custom Fields**
2. Add a new field:
   - **Label:** `Contract Value`
   - **Type:** Currency
   - **Applies to:** All agreements
3. Add another field:
   - **Label:** `Business Unit`
   - **Type:** Dropdown
   - **Options:** Sales, Legal, Finance, Operations

---

### Step 4 — Set a Renewal Reminder

1. Open the agreement you uploaded in Step 2
2. Click **Actions > Set Reminder**
3. Configure:
   - **Reminder:** 60 days before expiration
   - **Notify:** agreement owner + assigned reviewer
4. Save the reminder

---

### Step 5 — Collaborate with Reviewers

1. Open the agreement detail page
2. Click **Invite Reviewer**
3. Enter a colleague's email address
4. Add a note: `Please review Section 3 before renewal decision`
5. The reviewer will receive an email notification with a link to the agreement

---

## Demo Agreements

Sample files for hands-on practice are in the [`demo-agreements/`](./demo-agreements/) folder:

| File | Description |
|------|-------------|
| `vendor-nda-signed.pdf` | Completed vendor NDA for import and lifecycle practice |
| `msa-template.pdf` | Master Service Agreement template |
| `sow-example.pdf` | Statement of Work example with key fields |
| `renewal-ready-contract.pdf` | Contract approaching renewal date (for reminder lab) |

---

## Troubleshooting

| Issue | Resolution |
|-------|-----------|
| Agreement Desk not visible | Feature may need to be enabled by your Docusign account admin under Settings |
| Cannot upload agreement | Check file size limit (max 25MB) and supported formats (PDF, DOCX) |
| Reminder email not received | Check spam folder; verify notification settings under your profile |

---

## Next Step

Proceed to [AI-Assisted Review](../05-AI-AR/AI-AR.md)
