# AI-Assisted Review (AI-AR)

This module covers Docusign's **AI-Assisted Review** capabilities — using AI to analyze agreements, extract key data, and surface risks automatically.

---

## Overview

**AI-AR** (AI-Assisted Review) helps legal, procurement, and operations teams:

- Automatically extract key terms (dates, parties, payment terms, governing law)
- Flag non-standard or risky clauses for human review
- Summarize long agreements in plain language
- Compare agreement language against approved playbooks
- Reduce manual review time significantly

---

## Key Concepts

| Concept | Description |
|---------|-------------|
| **Extraction** | AI reads the document and pulls structured data (dates, entities, amounts) |
| **Risk Scoring** | AI assigns a risk level based on detected clause language |
| **Playbook** | Your organization's standard acceptable language that AI compares against |
| **Deviation** | A clause that differs from your playbook standards |
| **Navigator** | Docusign's AI product that powers agreement intelligence at scale |

---

## Lab Steps

### Step 1 — Enable AI Review on an Agreement

1. Open an agreement in **Agreement Desk**
2. Click **AI Review** in the right panel
3. Click **Run AI Analysis**
4. Wait for the analysis to complete (typically 10–30 seconds)

> Screenshot placeholder: `../assets/images/05-ai-review-panel.png`

---

### Step 2 — Review Extracted Fields

After analysis completes, review the extracted fields:

1. Expand the **Extracted Data** section
2. Verify or correct AI-extracted values:
   - Effective Date
   - Expiration Date
   - Governing Law
   - Payment Terms
   - Auto-Renewal clause (yes/no)
3. Click **Confirm** on correct fields, or **Edit** to correct any errors

---

### Step 3 — Review Flagged Clauses

1. Click the **Flagged Clauses** tab
2. You will see a list of clauses the AI flagged as:
   - High Risk (red)
   - Medium Risk (yellow)
   - Deviation from Playbook (orange)
3. Click any flagged clause to see:
   - The original contract text
   - The AI's reasoning
   - The playbook standard text (if configured)
4. Mark each clause as **Accepted**, **Needs Revision**, or **Escalate**

---

### Step 4 — Generate a Summary

1. Click **Generate Summary**
2. The AI produces a plain-language summary covering:
   - Parties involved
   - Core obligations
   - Key dates and amounts
   - Notable risks or deviations
3. Copy or export the summary for your records

---

### Step 5 — Use the Docusign Navigator API

You can also call AI-AR capabilities programmatically via the **Docusign Navigator API**.

#### Sample API Request — Analyze a Document

```bash
curl -X POST "https://api.docusign.com/v1/accounts/{accountId}/navigator/documents" \
  -H "Authorization: Bearer {accessToken}" \
  -H "Content-Type: application/json" \
  -d '{
    "documentUrl": "https://your-storage.example.com/contract.pdf",
    "analysisTypes": ["extraction", "riskScoring", "summary"]
  }'
```

#### Sample Response

```json
{
  "documentId": "abc123",
  "status": "processing",
  "estimatedCompletionSeconds": 20
}
```

#### Poll for Results

```bash
curl -X GET "https://api.docusign.com/v1/accounts/{accountId}/navigator/documents/abc123" \
  -H "Authorization: Bearer {accessToken}"
```

---

## Use Cases

| Use Case | How AI-AR Helps |
|----------|----------------|
| NDA Review | Instant extraction of parties, term length, confidentiality scope |
| MSA Renewal | Flags auto-renewal clauses and compares payment terms to playbook |
| Vendor Contracts | Surfaces indemnification and liability cap deviations |
| Employment Agreements | Identifies non-compete and IP assignment clauses |

---

## Troubleshooting

| Issue | Resolution |
|-------|-----------|
| AI Review button not visible | Ensure AI-AR is enabled for your account (contact your Docusign admin) |
| Extraction accuracy low | Works best on machine-readable PDFs; scanned documents may need OCR pre-processing |
| API returns 403 | Ensure your OAuth token includes the `adm_store_unified_repo_read` scope |

---

## Additional Resources

- [Docusign Navigator Documentation](https://developers.docusign.com/docs/navigator-api/)
- [AI-AR Playbook Configuration Guide](https://support.docusign.com)
- [Navigator API Reference](https://developers.docusign.com/docs/navigator-api/reference/)

---

## Workshop Complete

Congratulations on completing all five modules! Review the [Glossary](../GLOSSARY.md) and [Resources](../resources/Resources.md) for next steps.
