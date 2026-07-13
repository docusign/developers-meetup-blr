![docusign-developers-logo](https://raw.githubusercontent.com/docusign/developers-meetup-blr/a271c616b0c6e69da79e90eda7ebea44ca0eed8a/assets/images/01-docusign_developers_lockup_387x50.svg)

# Connecting Anthropic (Claude) with Docusign MCP Server

As a part of this workshop, we will be setting up a Custom Connector with Claude to connect Docusign MCP server.

---

## Overview

**Docusign MCP Server** allows you to interact with your Docusign account to view account details, send envelopes, trigger workflows and [much more](https://developers.docusign.com/platform/mcp-server/#available-tools).

---

## Flow

```
  Open Claude Web UI
        |
        v
  Add Custom Connector
        |
        v
  Enter Server URL, Client ID, and Client Secret
        |
        v
  Save Connection
        |
        v
  Authorize the connection after reviewing the scopes
        |
        v
  Run a test prompt

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
