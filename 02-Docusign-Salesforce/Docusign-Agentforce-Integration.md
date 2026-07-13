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
  
## Install the Docusign Salesforce Connector

- [ ] Step 1. Select **App launcher** (nine dots icons).
- [ ] Step 2. Select **View All**.
- [ ] Step 3. Select **Visit AppExchange**.
- [ ] Step 4. Select **Go to AppExchange**.
- [ ] Step 5. Search for **Docusign eSignature for Salesforce.**
- [ ] Step 6. Select **Get It Now** → Install in your Salesforce Developer org.
- [ ] Step 7. Sign in to your Docusign org (if required).
- [ ] Step 8. Select **Install for All Users** → select **Install.**
- [ ] Step 9. Approve third-party access if prompted → click **Continue.**

## Configure Docusign Connection

- [ ] Step 1. Go to **App Launcher** → search for **Docusign.**
- [ ] Step 2. Select **Docusign Apps Launcher.**
- [ ] Step 3. Click **Connect to Docusign** and log in with your Docusign developer account
- [ ] Step 4. Authorize the Salesforce integration when prompted.
- [ ] Step 5. Confirm the connection status shows **Connected Account.**

## Create Apex Classes

- [ ] Step 1. 
- [ ] Step 2. 
- [ ] Step 3. 
- [ ] Step 4. 
- [ ] Step 5. 

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
