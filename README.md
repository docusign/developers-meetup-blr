# Docusign Developer Workshop

Welcome to the **Docusign Developer Workshop** repository. This repo contains hands-on labs, guides, and resources for developers learning to build with Docusign APIs and integrations.

## Workshop Modules

| Module | Topic | Description |
|--------|-------|-------------|
| [01 - Overview](./01-Overview/Overview.md) | Workshop Overview | Goals, structure, and what to expect |
| [02 - Docusign Salesforce](./02-Docusign-Salesforce/Docusign-Agentforce-Integration.md) | Agentforce Integration | Connect Docusign with Salesforce Agentforce |
| [03 - Workflow Builder](./03-Workflow-Builder/Workflow-Builder.md) | Workflow Builder | Build automated document workflows |
| [04 - Agreement Desk](./04-Agreement-Desk/Agreement-Desk.md) | Agreement Desk | Manage and track agreements end-to-end |
| [05 - AI-AR](./05-AI-AR/AI-AR.md) | AI-Assisted Review | Leverage AI for agreement review and analysis |

## Quick Start

1. Review the [Prerequisites](./01-Overview/Prerequisites.md) before starting
2. Follow modules in order (01 → 05)
3. Reference the [Glossary](./GLOSSARY.md) for terminology
4. See [Resources](./resources/Resources.md) for useful links and tools

## Repository Structure

```
docusign-developer-workshop/
├── README.md
├── GLOSSARY.md
├── 01-Overview/
│   ├── Overview.md
│   └── Prerequisites.md
├── 02-Docusign-Salesforce/
│   └── Docusign-Agentforce-Integration.md
├── 03-Workflow-Builder/
│   ├── Workflow-Builder.md
│   └── exports/               # Exported workflow JSON/YAML files
├── 04-Agreement-Desk/
│   ├── Agreement-Desk.md
│   └── demo-agreements/       # Sample agreements for hands-on labs
├── 05-AI-AR/
│   └── AI-AR.md
├── assets/
│   ├── images/                # Screenshots and diagrams used in guides
│   └── videos/                # Demo and walkthrough video files
└── resources/
    └── Resources.md           # Curated links, SDKs, and references
```

## Contributing

Please follow the existing folder/file naming conventions when adding content. Place screenshots in `assets/images/` and reference them using relative paths.
