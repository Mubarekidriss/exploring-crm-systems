# Exploring CRM Systems Using Generative AI

## Student Information

- **Student:** Mubarek Idris
- **Course:** ICS 499 - Software Engineering and Capstone Project
- **Assignment:** Exploring CRM Systems Using Generative AI

## Executive Summary

This project studies what customer relationship management (CRM) systems do, compares four commercial products and three open-source products, and proposes an architecture for a small CRM built with HTML, CSS, JavaScript, jQuery, Bootstrap, PHP, and MySQL. I used ChatGPT as a research assistant, then checked important claims against vendor documentation, product pages, and the instructor's assignment sheet.

Salesforce is the strongest enterprise choice in this comparison because it has the broadest platform and the largest CRM market share. For a small business that wants a hosted system, I would start with HubSpot because the free entry point is simple. For a company that wants to control its own data, I would choose SuiteCRM because it is mature, has the expected sales modules, and includes reporting without requiring a separate paid reporting add-on.

## AI Tools Used

I used ChatGPT to:

- make an initial research plan;
- suggest comparison criteria;
- summarize technical documentation;
- propose an MVP architecture;
- check whether the report answered every requirement.

I did not treat AI output as a final source. Product claims and technical requirements were checked against the links in [references.md](references.md). The exact prompts and my evaluation are in [prompts_used.md](prompts_used.md).

## CRM Research Findings

A CRM gives sales, marketing, and support teams one place to track people, organizations, conversations, activities, and business opportunities. It replaces scattered spreadsheets and inbox notes with shared records and a repeatable process. The detailed explanation, history, industry examples, and module descriptions are in [crm_research.md](crm_research.md).

## CRM Product Comparisons

The commercial comparison covers:

- Salesforce Sales Cloud
- HubSpot CRM / Sales Hub
- Zoho CRM
- Microsoft Dynamics 365 Sales

The open-source comparison covers:

- SuiteCRM
- EspoCRM
- Odoo Community CRM

The tables and recommendations are in [crm_research.md](crm_research.md).

## Open Source CRM Evaluation

I selected **SuiteCRM** for the hands-on evaluation. It has Contacts, Leads, Accounts, Opportunities, dashboards, and a built-in Reports module, so it can produce all five views requested by the assignment. Two setup paths are included:

- [Docker guide](install-guides/docker.md) - fastest route for the assignment
- [XAMPP guide](install-guides/xampp.md) - manual Windows route using Apache, MariaDB, and PHP

**Current status:** the research and setup guides are complete. The actual local installation and evaluation must be completed on the student's computer. The five files in `screenshots/` are placeholders, not screenshots. After the install, replace each placeholder with a real PNG using the same filename and complete the observation fields in the [evaluation worksheet](open_source_evaluation.md).

## CRM Architecture Proposal

The proposed system has a Bootstrap/jQuery browser interface, PHP controllers and services, a MySQL data layer, and supporting email, logging, and background-job services. It includes authentication, role-based authorization, contacts, accounts, leads, opportunities, activities, tasks, and basic reports.

![CRM architecture diagram](architecture/crm_architecture.png)

The full module, table, library, security, and MVP explanation is in [crm_research.md](crm_research.md#part-4---ai-assisted-crm-architecture-exploration).

## Prompt Engineering Examples

The prompts were strongest when they named a role, business size, products, comparison fields, source requirements, and output format. Broad prompts gave broad answers and sometimes mixed current facts with old pricing. Five useful prompts and the full reflection are in [prompts_used.md](prompts_used.md).

## Lessons Learned

AI is useful for turning a large topic into a research plan and showing what questions I may be missing. It is weaker at facts that change, especially prices, versions, licensing, and installation requirements. I also learned that two products can both be called “open source” while offering different features in their free and paid editions. The best workflow was to use AI for structure, read the original documentation, correct the draft, and record the source.

## References

All research links and validation notes are in [references.md](references.md).

## Repository Map

```text
exploring_crm_systems/
├── README.md
├── crm_research.md
├── open_source_evaluation.md
├── prompts_used.md
├── references.md
├── architecture/
│   ├── crm_architecture.dot
│   └── crm_architecture.png
├── install-guides/
│   ├── docker.md
│   └── xampp.md
└── screenshots/
    ├── login.png
    ├── dashboard.png
    ├── contacts.png
    ├── leads.png
    └── reports.png
```
