![docusign-developers-logo](https://raw.githubusercontent.com/docusign/developers-meetup-blr/a271c616b0c6e69da79e90eda7ebea44ca0eed8a/assets/images/01-docusign_developers_lockup_387x50.svg)

# Docusign Developer Console

When building a Docusign integration, you must first create an app in the Dev Console to get your client ID. 
This client ID/Integration Key is required to call any Docusign API, either directly or by using an SDK.

Previously, you could create this using [Apps and Keys] (https://apps-d.docusign.com/admin/apps-and-keys) page in your Docusign Developer Account.

You can now create your Integration Key (IK) using Docusign Developer Console.

---

## Overview

**Docusign Developer Console** is Docusign's portal to generate client id for your app and share among the developers.

---

## Flow

```
Login Docusign Developer Console
        |
        v
  Create Client ID/Integration Key (IK)
        |
        v
  Generate Secret
        |
        v
  Set Redriect URI
        |
        v
  Note down IK, and Secret Values

```
---

# Docusign Developer Console

Follow the procedure to generate Integrtion Key (IK) through Developer Console:

## Login Docusign Developer Console Account

- [ ] Step 1: Go to <https://apps.docusign.com/dev-console/integrations>
- [ ] Step 2: Enter Email as ```docusigndevelopersworkshop@zohomail.in```
- [ ] Step 3: Select **Next**
- [ ] Step 4: Enter password as ```Docusign!```

## Add an Integration Key (IK)

- [ ] Step 1: Select **+ Add**
- [ ] Step 2: Enter your firstname and lastname as ```firstname.lastname```
- [ ] Step 3: Select **Create**
- [ ] Step 4: Note the Client ID (to be used in Claude LLM)

## Generate Secret and Set Redirect URI

- [ ] Step 1: Select **Third-party client ID**
- [ ] Step 2: Select **+Add** under Client Secret.
- [ ] Step 3: Note the Client Secret (to be used in Claude LLM)
- [ ] Step 4: Select **+Add** under Redirect URI.
- [ ] Step 5: Enter both the urls:
              https://claude.ai/api/mcp/auth_callback
              https://claude.com/api/mcp/auth_callback
- [ ] Step 6: Select **Save**

 ![Redirect_URI](https://raw.githubusercontent.com/docusign/developers-meetup-blr/refs/heads/main/assets/videos/Add_Redirect_URI.webp)
