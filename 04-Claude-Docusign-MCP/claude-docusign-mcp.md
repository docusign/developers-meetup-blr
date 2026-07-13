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

Follow the procedure to Connect Claude with Docusign MCP Server:

## Add a Custom Connector

- [ ] Step 1: Go to [Claude Web](https://claude.ai/).
- [ ] Step 2: Open a new chat and select **+**.
- [ ] Step 3: Select **Add Connector -> ...Add custom connector**
- [ ] Step 4: Enter a name for the Connector say ```Docusign MCP```
- [ ] Step 5: Enter **Remote MCP server URL** as ```https://mcp-d.docusign.com/mcp```
- [ ] Step 6: Enter the **Client ID**
- [ ] Step 7: Enter the **Client Secret**
- [ ] Step 8: Select **Add**

## Connect and Authorize Connector

- [ ] Step 1: Select **Connect**
- [ ] Step 2: Select **Allow Access** after reviewing the listed scopes of the created connector.
- [ ] Step 3: Ensure Connector is available under **Add Connector** menu.

## Run a test prompt

- [ ] Step 1: Enter the following prompt: ```List my Docusign account details and list of available tools```
- [ ] Step 2: Select **Allow Access** (if prompted)

Your Docusign account details are displayed along with the list of available MCP tools. 

> Please leave this tab open. We will build the workflow in the next step, and then use Claude to trigger it immediately after.

 ---
## Next Step

Proceed to [Workflow Builder](../05-Workflow-Builder/Workflow-Builder.md)
