# Docusign Agentforce Integration

This module walks you through integrating Docusign with Salesforce Agentforce, enabling Agentforce agents to trigger, creating agent's actions, monitor, and act on agreement events autonomously.

---

## Overview

**Agentforce** is Salesforce's platform for building autonomous AI agents.

---

## Architecture

```
Salesforce Agentforce Agent
        |
        v
  Agentforce action / Apex Action
        |
        v
  Named Credential (OAuth 2.0)
        |
        v
  Workflow Builder
        |
        v
  Agreement posted in Agreement Desk

```
---

# Docusign Agentforce Integration

Follow the procedure to use Agentforce with Docusign Account:

## Sign Up for a Salesforce Developer Account

- [ ] Step 1. Go to <https://developer.salesforce.com/signup>
- [ ] Step 2. Fill in your first name, last name, job title, company, country, work email, and username (must be in email format, e.g. `yourname@comany.com`)
- [ ] Step 3. Select **Sign me up.**
- [ ] Step 4. Check your email and click the verification link.
- [ ] Step 5. Set your password and log in to your Salesforce org.
- [ ] Step 6. Select Remind Later if prompted for your mobile number.

## Enable Agentforce

- [ ] Step 1. Go to **Setup** → search for **Agents** in the Quick Find box
- [ ] Step 2. Select **Agentforce Agents** under **Einstein** menu.
- [ ] Step 3. Toggle **Agentforce** to **ON.**
- [ ] Step 4. Accept any terms and wait for provisioning to complete (if prompted).
  
## Install the Docusign Salesforce Connector (To view the status of envelopes and agreements from your Docusign account)

- [ ] Step 1. Select **App launcher** (nine dots icons).
- [ ] Step 2. Select **View All**.
- [ ] Step 3. Select **Visit AppExchange**.
- [ ] Step 4. Select **Go to AppExchange**.
- [ ] Step 5. Search for **Docusign eSignature for Salesforce.**
- [ ] Step 6. Select **Get It Now** → Install in your Salesforce Developer org.
- [ ] Step 7. Sign in to your Docusign org (if required).
- [ ] Step 8. Select **Install for All Users** → select **Install.**
- [ ] Step 9. Approve third-party access if prompted → click **Continue.**

## Configure Docusign Connection (Sign in your Docusign Account)

- [ ] Step 1. Go to **App Launcher** → search for **Docusign.**
- [ ] Step 2. Select **Docusign Apps Launcher.**
- [ ] Step 3. Click **Connect to Docusign** and log in with your Docusign developer account
- [ ] Step 4. Authorize the Salesforce integration when prompted.
- [ ] Step 5. Confirm the connection status shows **Connected Account.**

## Create Named Credentials (To allow Agentforce to interact with your Docusign Account-Credentials are stored in encrypted form)

- [ ] Step 1. Log into your **Docusign developer** account.
- [ ] Step 2. Go to **Admin → Integrations → Apps and Keys**.
- [ ] Step 3. Click **Add App and Integration Key**.
- [ ] Step 4. Name the app (e.g., **Salesforce Named Credential**) and **Save**.
- [ ] Step 5. Copy the **Integration Key (Client ID)**.
- [ ] Step 6. Under **Actions → Edit → Add** Secret key, generate and copy the Client Secret.
- [ ] Step 7. Add a **Redirect URI placeholder** (we’ll update it after we have the Salesforce callback):

For sandbox:
https://test.salesforce.com/services/authcallback/Docusign

For production:
https://login.salesforce.com/services/authcallback/Docusign

You will later replace Docusign with the exact URL Suffix from the Salesforce Auth Provider.

## Create Salesforce Auth Provider (OpenID Connect)

- [ ] Step 1. In **Salesforce Setup**, search for **Auth. Providers**.
- [ ] Step 2. Click **New**, select **Open ID Connect**.
- [ ] Step 3. Fill in:
* **Name**: Docusign
* **URL Suffix**: Docusign
* **Consumer Key**: your Integration Key
* **Consumer Secret**: your Client Secret
* **Authorize Endpoint URL (demo)**: https://account-d.docusign.com/oauth/auth
* **Token Endpoint URL (demo)**: https://account-d.docusign.com/oauth/token
* **User Info Endpoint URL (demo)**: https://account-d.docusign.com/oauth/userinfo
* Default Scopes: e.g.signature extended aow_manage impersonation            
- [ ] Step 4. Check:
* **Send access token in header**
* **Include Consumer Secret in API Responses**
- [ ] Step 5. **Save** the Auth Provider.
- [ ] Step 6: Copy the generated **Callback URL**.
- [ ] Step 7: Go back to **Docusign Admin → Apps and Keys → your app → Edit:**
* Replace the placeholder redirect URI with this **Callback URL**.
* **Save**.
- [ ] Step 8: From the Auth Provider detail page, click **Test‑Only Initialization URL** and confirm you can:
* Log into Docusign
* Return to Salesforce without error.

## Create External Credential (Browser Flow)

- [ ] Step 1. In **Setup → Named Credentials → External Credentials**, click **New**.
- [ ] Step 2. Configure:
* **Label**: DocusignExternalCredential
* **Name**: DocusignExternalCredential
* **Authentication Protocol**: OAuth 2.0
* **Authentication Flow Type**: Browser Flow
* **Scope**: signature extended aow_manage impersonation (or your chosen scopes)
* **Authentication Provider**: select the **Docusign** Auth Provider from step 2.
- [ ] Step 3. Save

## Configure Principal

- [ ] Step 1. On the DocusignExternalCredential detail page, scroll to **Principals**.
- [ ] Step 2. Click **New** and configure:
* **Parameter Name**: DocusignNamedPrincipal
* **Identity Type**: Named Principal (org‑wide token) or Per User Principal (per user auth)
* **Scope**: signature extended aow_manage impersonation

You will authenticate this principal later using Browser Flow. (Important to not miss)

## Create an Agentforce Agent

- [ ] Step 1. Go to **Setup** → search for **Agents**
- [ ] Step 2. Click **New Agent**
- [ ] Step 3. Select **Custom Agent** as the type
- [ ] Step 4. Give it a name: `DocuSign Assistant`
- [ ] Step 5. Set the description: `Helps users send and track DocuSign envelopes`
- [ ] Step 6. Click **Next** → **Save**

## Create Agent Actions

- [ ] Step 1. Open the agent you just created → click **Agent Actions**
- [ ] Step 2. Click **New Agent Action**
- [ ] Step 3. Select **Apex** as the action type
- [ ] Step 4. Choose the `` Apex class
- [ ] Step 5. Map the input and output parameters as instructed by the facilitator
- [ ] Step 6. Click **Save**
- [ ] Step 7. Repeat for any additional actions

## Configure Agent Topics

- [ ] Step 1. In the agent, click **Topics**
- [ ] Step 2. Click **New Topic**
- [ ] Step 3. Name it `Send Agreement` and add a description that guides the agent when to use this topic
- [ ] Step 4. Assign the relevant Agent Actions created in Step 7
- [ ] Step 5. Click **Save**

## Activate the Agent

- [ ] Step 1. Open your agent → click **Activate**
- [ ] Step 2. Confirm the activation dialog
- [ ] Step 3. Verify the agent status changes to **Active**

## Create Sample Records

- [ ] Step 1. Go to **App Launcher** → open **Accounts**
- [ ] Step 2. Click **New** → create a sample account (e.g. `Acme Corp`)
- [ ] Step 3. Go to **Contacts** → click **New** → create a contact linked to `Acme Corp`
- [ ] Step 4. Add a valid email address to the contact (this will receive the DocuSign envelope)
- [ ] Step 5. Go to **Opportunities** → click **New** → create an opportunity linked to `Acme Corp`


## Test Agentforce

1. Go to **App Launcher** → open the **Agent** or use the **Einstein** icon in the bottom right
2. Type a prompt such as: ``
3. Confirm the agent identifies the correct action and contact
4. Approve the action → verify the envelope is sent
5. Check the contact's email for the DocuSign envelope

## Troubleshooting

| Issue                 | Fix                                                              |
| --------------------- | ---------------------------------------------------------------- |
| Agent not responding  | Check that the agent is **Active** and the topic is configured   |
| Apex class errors     | Verify the class compiled without errors in Setup → Apex Classes |
| DocuSign not sending  | Check the DocuSign connection status in DocuSign Admin           |
| Envelope not received | Confirm the contact has a valid email address                    |

> **Facilitator note:** Replace placeholder class names and install URLs with the actual resources before distributing this guide.


---

## Next Step

Proceed to [Connecting Claude with Docusign MCP Server](../04-Claude-Docusign-MCP/claude-docusign-mcp.md)
