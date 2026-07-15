# Docusign Developers Meetup — Bangalore

> Hands-on labs, guides, and resources for developers building with Docusign APIs and integrations.

---

## Overview

This repository contains workshop materials from the **Docusign Developers Meetup – Bangalore**, covering two progressive workshop modules. Each workshop is self-contained with structured labs, presenter resources, and reference materials.

---

## Workshops

### Workshop 1 Architect AI-Powered Agreement Automation

Use Agentforce and Docusign IAM to automate agreement workflows from your CRM—trigger contract generation from Salesforce, route with Workflow Builder, and apply AI-Assisted Review to reduce manual legal reviews.

| Module | Topic |
|--------|-------|
| `01-Overview` | Prerequisites, architecture overview, and workshop orientation |
| `02-Salesforce Docusign Agentforce` | Integrating Docusign with Salesforce's Agentforce AI platform |
| `03-Developer-Console` | Setting up and navigating the Docusign Developer Console |
| `04-Claude-Docusign-MCP` | Connecting Claude AI to Docusign via Model Context Protocol (MCP) |
| `05-Workflow-Builder` | Building automated document workflows using the Workflow Builder |

**Assets & Resources:**
- `assets/` — Supporting images and media
- `resources/` — Reference links, SDKs, and sample demo agreements

> Follow modules sequentially. Refer to [`GLOSSARY.md`](./GLOSSARY.md) for terminology reference.

---

### Workshop 2 Docusign Manage: From Static PDFs to Agentic Workflows

A hands-on session designed for cross-functional teams (procurement, finance, legal, operations) and technical builders (developers and architects). It covers transforming static PDF documents into intelligent, agentic workflows using Docusign Manage.

**Session Structure:**

| File | Purpose |
|------|---------|
| `index.html` | Workshop landing page with navigation |
| `1_Run_of_Show.html` | Presenter agenda with timing and narrative framing |
| `2_Hands_on_Flow.html` | Step-by-step lab exercise |
| `SPEAKER_NOTES.md` | Presenter guidance and talking points |
| `Docusign_Manage_Workshop_RunOfShow.xlsx` | Detailed run sheet with timing |

**Lab Flow:**

1. **CLI Authentication** — Log in via the Docusign Agreement CLI (`ds` command)
2. **Bulk Upload** — Ingest documents in bulk into Docusign Manage
3. **Field Extraction** — Extract structured data using Docusign Navigator / Agreement Manager
4. **MCP Integration** — Connect Docusign to Copilot Studio via Model Context Protocol
5. **Agent Studio Demo** — Showcase agentic workflow automation end-to-end

---

## Repository Structure

```
developers-meetup-blr/
├── Workshop-1/
│   ├── 01-Overview/
│   ├── 02-Salesforce Docusign Agentforce/
│   ├── 03-Developer-Console/
│   ├── 04-Claude-Docusign-MCP/
│   ├── 05-Workflow-Builder/
│   ├── assets/
│   ├── resources/
│   └── Readme.md
├── Workshop-2/
│   ├── assets/                  # Brand assets (logos, DSIndigo typeface)
│   ├── workshop-resources/
│   ├── index.html
│   ├── 1_Run_of_Show.html
│   ├── 2_Hands_on_Flow.html
│   ├── SPEAKER_NOTES.md
│   ├── Docusign_Manage_Workshop_RunOfShow.xlsx
│   ├── .nojekyll
│   └── READMe.md
├── GLOSSARY.md
└── README.md
```

---

## Key Technologies Covered

- **Docusign eSignature API** — Electronic signature collection and envelope management
- **Docusign Agreement Manager** — AI-powered data and field extraction from agreements
- **Docusign Workflow Builder** — Visual automation tool for document routing
- **Docusign Agreement CLI** — Command-line tool (`ds`) for agreement type configuration and bulk ingestion
- **Docusign Agentforce Integration** — Salesforce's autonomous AI agent platform
- **Model Context Protocol (MCP)** — Standard for connecting AI models (Claude, Copilot Studio) to Docusign
- **OAuth 2.0** — Authorization standard for Docusign integrations

---

## Glossary

A comprehensive terminology reference is available in [`GLOSSARY.md`](./GLOSSARY.md), covering key terms such as Agentforce, CLM, Envelope, Agreement Manager (Formerly Navigator), OAuth 2.0, Webhooks, Workflow Builder (Formerly Maestro), and more.

---

## Resources

- [Docusign Developer Center](https://developers.docusign.com)
- [Docusign Agreement CLI Docs](https://developers.docusign.com/tools/agreement-cli/)
- [Model Context Protocol](https://modelcontextprotocol.io)
- [Docusign Sandbox / Demo Account](https://www.docusign.com/developers/sandbox?postActivateUrl=https%3A%2F%2Fdevelopers.docusign.com%2F)

---


