# Docusign Agentforce Integration

This module walks you through integrating Docusign with Salesforce Agentforce, enabling AI agents to trigger, monitor, and act on agreement events autonomously.

---

## Overview

**Agentforce** is Salesforce's platform for building autonomous AI agents. By connecting Docusign to Agentforce, you can:

- Trigger envelope sends from within an AI agent conversation
- Surface agreement status and data inside Salesforce records
- Automate follow-ups when agreements are signed, declined, or expired
- Use agreement data as context for agent reasoning

---

## Architecture

```
Salesforce Agentforce Agent
        |
        v
  Salesforce Flow / Apex Action
        |
        v
  Named Credential (OAuth 2.0)
        |
        v
  Docusign eSignature API
        |
        v
  Webhook / Connect → Salesforce Platform Event
        |
        v
  Agentforce reacts to Platform Event
```

> Screenshot placeholder: `../assets/images/02-architecture-diagram.png`

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
