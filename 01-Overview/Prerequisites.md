# Prerequisites

Complete all setup steps below **before** attending the workshop. Each module assumes these are already in place.

---

## 1. Accounts Required

| System | Type | Notes |
|--------|------|-------|
| Docusign | Developer Sandbox | Free at [developer.docusign.com](https://developer.docusign.com) |
| Salesforce | Developer Org or Sandbox | Free at [developer.salesforce.com](https://developer.salesforce.com) |
| GitHub | Free account | To clone/fork this repo |

---

## 2. Docusign Setup

- [ ] Sign up for a **Docusign Developer account** at https://developer.docusign.com
- [ ] Log in to your Docusign sandbox (`account-d.docusign.com`)
- [ ] Create an **Integrations Key (Client ID)** under Settings > Apps and Keys
- [ ] Note your **Account ID** (GUID format, found in Settings > Apps and Keys)
- [ ] Enable **Workflow Builder** in your account (Settings > Workflow Builder)
- [ ] Enable **Agreement Desk** if available in your sandbox tier

---

## 3. Salesforce Setup

- [ ] Provision a **Salesforce Developer Edition** org or sandbox
- [ ] Enable **Agentforce** in your org (Setup > Agentforce)
- [ ] Install the **Docusign for Salesforce** managed package
  - AppExchange listing: https://appexchange.salesforce.com (search "Docusign eSignature")
- [ ] Configure a **Named Credential** for Docusign API calls
- [ ] Assign yourself the **Docusign Administrator** permission set

---

## 4. Local Development Tools

- [ ] **Git** — https://git-scm.com
- [ ] **Salesforce CLI (SF CLI)** — https://developer.salesforce.com/tools/salesforcecli
- [ ] **VS Code** with Salesforce Extension Pack — https://marketplace.visualstudio.com/items?itemName=salesforce.salesforcedx-vscode
- [ ] A REST client such as **Postman** or **Insomnia** (optional, for API exploration)

---

## 5. Clone This Repository

```bash
git clone https://github.com/<your-org>/docusign-developer-workshop.git
cd docusign-developer-workshop
```

---

## 6. Verify Access

Before the workshop starts, confirm you can:

1. Log in to your Docusign sandbox and see the dashboard
2. Log in to your Salesforce org and navigate to Setup
3. View the Docusign for Salesforce app in the App Launcher

---

## Need Help?

Contact your workshop facilitator or refer to the [Resources](../resources/Resources.md) page for documentation links.
