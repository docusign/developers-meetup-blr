# Workshop 1 Architect AI-Powered Agreement Automation

> Hands-on labs for building intelligent agreement workflows with Docusign APIs, Salesforce Agentforce, and Claude AI via the Model Context Protocol (MCP).

---

## Overview

This workshop introduces developers to Docusign's **Intelligent Agreement Management** platform through a structured, progressive set of hands-on modules. Participants configure real integrations from setting up a Developer Console and connecting Claude via MCP, to building automated workflows in approximately **70 minutes**.

---

## Target Audience

| Role | Relevance |
|------|-----------|
| Salesforce Developers | Agentforce + Docusign integration patterns |
| Solution Builders | Workflow automation with no-code tools |
| Integration Engineers | MCP server setup, OAuth, API configuration |
| Technical Consultants | End-to-end agreement lifecycle management |

---

## Prerequisites

Before the session, ensure you have the following accounts set up and verified:

| Requirement | Details |
|-------------|---------|
| **Docusign Developer Sandbox** | Free account at [Docusign Developer Account](https://www.docusign.com/developers/sandbox?postActivateUrl=https%3A%2F%2Fdevelopers.docusign.com%2F) |
| **GitHub** | Access to this repository |
| **Claude (Anthropic)** | Access to [claude.ai](https://claude.ai) |

**Before the session starts:**
1. Create all accounts and verify your email addresses
2. Locate your **8-digit Docusign Account ID** from your Docusign profile settings
3. Share your Account ID with a workshop volunteer before the session begins
4. Confirm you can log into all three platforms

> See [`01-Overview/Prerequisites.md`](./01-Overview/Prerequisites.md) for detailed setup instructions.

---

## Workshop Modules

```
Workshop-1/
├── 01-Overview/
├── 02-Salesforce Docusign Agentforce/
├── 03-Developer-Console/
├── 04-Claude-Docusign-MCP/
├── 05-Workflow-Builder/
├── assets/
└── resources/
```

### Module 01 — Overview
**Files:** `Overview.md`, `Prerequisites.md`

Sets the stage for the full workshop. Covers:
- Workshop goals and learning outcomes
- Required accounts and pre-session setup checklist

---

### Module 02 — Salesforce + Docusign Agentforce
**Files:** `demo_steps.md`

A live demonstration of the Docusign Agent embedded in Salesforce using Agentforce.

**Demo Flow:**
1. Launch the Docusign Agent and query renewal accounts
2. Navigate to a sample account opportunity
3. Agent generates a pre-populated web form using Salesforce data
4. Verify and submit the form
5. Open Agreement Desk to collaborate and finalize before sending for signature

> A demo video (no audio) is available in [`assets/videos/Docusign-Agentforce-Demo.mp4`](./assets/videos/Docusign-Agentforce-Demo.mp4)

---

### Module 03 — Developer Console Setup
**Files:** `developer-console.md`

Walks through obtaining a **Client ID (Integration Key)** and **Client Secret** from the Docusign Developer Console required for all API calls.

**Key Steps:**
1. Log in to the Docusign Developer Console
2. Create a new integration to generate a unique Client ID
3. Generate a Client Secret
4. Configure Redirect URIs for Claude MCP integration:
   - `https://claude.ai/api/mcp/auth_callback`
   - `https://claude.com/api/mcp/auth_callback`

> The Client ID and Client Secret generated here are used in Module 04.

---

### Module 04 — Claude + Docusign via MCP
**Files:** `claude-docusign-mcp.md`

Connects **Anthropic's Claude** to Docusign using the **Model Context Protocol (MCP)** server — enabling Claude to send envelopes, trigger workflows, and query account data through natural language.

**Setup Steps:**
1. Open Claude's web interface and navigate to custom connectors
2. Create a new connector named `Docusign MCP`
3. Enter the MCP server URL: `https://mcp-d.docusign.com/mcp`
4. Input the Client ID and Client Secret from Module 03
5. Authorize and grant access permissions
6. Verify by prompting Claude for your account details and available tools

**What you can do via MCP:**
- View account and envelope information
- Send documents for signature
- Trigger automated workflows
- Perform account-level operations — all from natural language prompts

---

### Module 05 — Workflow Builder
**Files:** `Workflow-Builder.md`, `exports/README.md`, `exports/` (JSON templates)

Docusign Workflow Builder is a **visual, no-code platform** for designing automated agreement processes.

**Core Concepts:**

| Component | Description |
|-----------|-------------|
| **Triggers** | Events that start a workflow (form submission, API call, schedule) |
| **Steps** | Actions in the workflow (send envelope, pause, notify) |
| **Conditions** | Logic branches based on field values or recipient actions |
| **Participants** | Dynamically resolved signers and approvers |

**Lab Exercise — Vendor Onboarding NDA:**
1. Create a new workflow with a Web Form trigger
2. Map participant fields (vendor name, email, company)
3. Add conditional branching based on envelope status (Signed / Declined)
4. Publish and test using the built-in test mode

**Pre-built Workflow Templates (in `exports/`):**

| Template | Description |
|----------|-------------|
| Vendor NDA Workflow | Conditional routing based on signature status |
| Employee Onboarding | Multi-document sequential signing |
| Procurement Approval | Manager escalation with approval gates |

**To import a template:**
1. Go to Workflow Builder in your sandbox
2. Upload the JSON file from the `exports/` folder
3. Re-link document templates (template IDs are account-specific)
4. Update any webhook URLs for your environment

---

## Assets

### `assets/images/`
Screenshots and diagrams used throughout the workshop guides.

### `assets/videos/`
| File | Description |
|------|-------------|
| `Docusign-Agentforce-Demo.mp4` | End-to-end Agentforce + Docusign demo (Module 02) |
| `Add_Redirect_URI.webp` | Animated guide for adding redirect URIs (Module 03) |


---

## Resources

See [`resources/Resources.md`](./resources/Resources.md) for a full catalog. Quick links:

**Documentation**
- [Docusign Developer Center](https://developers.docusign.com)
- [eSignature REST API Docs](https://developers.docusign.com/docs/esign-rest-api/)
- [Docusign MCP Server](https://mcp-d.docusign.com/mcp)
- [Workflow Builder Docs](https://developers.docusign.com/docs/workflow-builder/)

**Sandbox & Testing**
- [Docusign Developer Sandbox](https://account-d.docusign.com)

**SDKs**
- Node.js, Python, Java, C# — available on [developers.docusign.com](https://developers.docusign.com/sdks-and-tools/)

**Authentication**
- OAuth 2.0 with JWT Grant Flow or Authorization Code Grant
- [OAuth documentation](https://developers.docusign.com/platform/auth/)

**Learning**
- [Docusign University](https://university.docusign.com)

---


## Getting Started

```bash
# 1. Clone the repository
git clone https://github.com/docusign/developers-meetup-blr.git
cd developers-meetup-blr/Workshop-1

# 2. Start with the overview
open 01-Overview/Overview.md

# 3. Complete prerequisites before the session
open 01-Overview/Prerequisites.md
```

Then follow the modules **in order** (01 → 05).

---

