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
- [ ] Step 4. Choose the `DocuSignEnvelopeAction` Apex class
- [ ] Step 5. Map the input and output parameters as instructed by the facilitator
- [ ] Step 6. Click **Save**
- [ ] Step 7. Repeat for any additional actions (e.g. check envelope status)

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
2. Type a prompt such as: `Send a DocuSign envelope to Acme Corp contact`
3. Confirm the agent identifies the correct action and contact
4. Approve the action → verify the envelope is sent
5. Check the contact's email for the DocuSign envelope
   {% endstep %}
   {% endstepper %}

## Troubleshooting

| Issue                 | Fix                                                              |
| --------------------- | ---------------------------------------------------------------- |
| Agent not responding  | Check that the agent is **Active** and the topic is configured   |
| Apex class errors     | Verify the class compiled without errors in Setup → Apex Classes |
| DocuSign not sending  | Check the DocuSign connection status in DocuSign Admin           |
| Envelope not received | Confirm the contact has a valid email address                    |

> **Facilitator note:** Replace placeholder class names and install URLs with the actual resources before distributing this guide.


---


## Lab Steps

### Step 1 — Configure OAuth Connection

1. In Salesforce, navigate to **Setup > Named Credentials**
2. Create a new Named Credential:
   - **Label:** `Docusign API`
   - **URL:** `https://demo.docusign.net/restapi`
   - **Identity Type:** Named Principal
   - **Authentication Protocol:** OAuth 2.0
3. Configure the Auth Provider pointing to your Docusign sandbox OAuth endpoint

> Screenshot placeholder: `../assets/images/02-named-credential.png`

---

### Step 2 — Create the Agentforce Action

1. Navigate to **Setup > Agent Actions**
2. Click **New Agent Action**
3. Select **Apex** as the action type
4. Reference the `DocusignSendEnvelopeAction` Apex class (provided in this module)
5. Define input parameters:
   - `templateId` (String) — Docusign Template ID
   - `recipientEmail` (String) — Recipient email address
   - `recipientName` (String) — Recipient full name
   - `recordId` (String) — Salesforce record ID for context

---

### Step 3 — Configure Docusign Connect (Webhook)

1. In your Docusign sandbox, go to **Settings > Connect**
2. Create a new Connect configuration:
   - **Name:** `Salesforce Platform Events`
   - **URL:** Your Salesforce Platform Event endpoint
   - **Trigger Events:** Envelope Sent, Envelope Completed, Envelope Declined
3. Note the Connect ID for reference

---

### Step 4 — Build the Agentforce Agent

1. Navigate to **Setup > Agentforce > Agents**
2. Click **New Agent**
3. Add the **Send Agreement** action created in Step 2
4. Write the agent topic and instructions:

```
Topic: Agreement Management
Instructions: When a user asks to send an agreement, collect the recipient's name and email,
confirm the template to use, then call the Send Agreement action.
Report the envelope ID back to the user.
```

5. Activate and test the agent in Agent Builder

---

## Sample Apex Action

```apex
public class DocusignSendEnvelopeAction {

    @InvocableMethod(label='Send Docusign Envelope' description='Sends a Docusign envelope from a template')
    public static List<Result> sendEnvelope(List<Request> requests) {
        List<Result> results = new List<Result>();
        for (Request req : requests) {
            // Call Docusign REST API via Named Credential
            HttpRequest httpReq = new HttpRequest();
            httpReq.setEndpoint('callout:Docusign_API/v2.1/accounts/' + req.accountId + '/envelopes');
            httpReq.setMethod('POST');
            httpReq.setHeader('Content-Type', 'application/json');
            // Build envelope JSON body (see Docusign eSignature REST API docs)
            // ...
            Http http = new Http();
            HttpResponse res = http.send(httpReq);
            Result r = new Result();
            r.envelopeId = (String) ((Map<String, Object>) JSON.deserializeUntyped(res.getBody())).get('envelopeId');
            results.add(r);
        }
        return results;
    }

    public class Request {
        @InvocableVariable(required=true) public String templateId;
        @InvocableVariable(required=true) public String recipientEmail;
        @InvocableVariable(required=true) public String recipientName;
        @InvocableVariable(required=true) public String accountId;
    }

    public class Result {
        @InvocableVariable public String envelopeId;
    }
}
```

---

## Testing

1. Open the Agentforce agent in the preview pane
2. Type: `Send a non-disclosure agreement to John Smith at john@example.com`
3. Confirm the agent collects required details and triggers the envelope send
4. Verify the envelope appears in your Docusign sandbox

---

## Troubleshooting

| Issue | Resolution |
|-------|-----------|
| 401 Unauthorized | Re-check Named Credential OAuth scopes — ensure `signature impersonation` is granted |
| Apex action not visible in Agent Builder | Ensure `@InvocableMethod` annotation is correct and class is deployed |
| Webhook not firing | Verify Docusign Connect URL and that your Salesforce org endpoint is publicly accessible |

---

## Next Step

Proceed to [Workflow Builder](../03-Workflow-Builder/Workflow-Builder.md)
