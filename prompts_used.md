# Prompts Used and AI Reflection

## AI Tool

I used **ChatGPT** as the AI research assistant for this assignment. I then checked product and technical claims against original sources listed in [references.md](references.md).

## Five useful prompts

### Prompt 1 - domain overview

```text
Act as a software consultant teaching a computer science student about CRM systems.
Explain CRM as both a business strategy and a software system. Cover its purpose,
history from contact databases to cloud and AI, and the roles of sales, marketing,
customer support, and analytics. Separate stable concepts from facts that need a source.
Use plain language and a short timeline.
```

**Why it worked:** The role, audience, topics, and output format were clear. Asking it to separate stable concepts from source-dependent facts made validation easier.

### Prompt 2 - commercial comparison

```text
Compare Salesforce Sales Cloud, HubSpot CRM/Sales Hub, Zoho CRM, and Microsoft
Dynamics 365 Sales. Use a table with target customer, strengths, weaknesses, and
pricing model. Do not guess current prices. Mark every price, edition, market-share,
and AI feature claim as needing verification on an official product page.
```

**Why it worked:** Naming the exact products and required table columns matched the assignment. The warning about current information reduced false precision.

### Prompt 3 - open-source comparison

```text
Compare SuiteCRM, EspoCRM, and Odoo Community CRM for a student evaluation.
For each product, list core CRM features, programming language, database,
community/support evidence, installation difficulty, license, and any important
feature that is paid rather than included in the free open-source edition.
Return a checklist of original documentation pages I should verify.
```

**Why it worked:** This prompt asked about edition boundaries, which exposed an important issue: EspoCRM's full Reports feature is part of the Advanced Pack.

### Prompt 4 - architecture and security

```text
Design a minimum viable CRM using HTML, CSS, JavaScript, jQuery, Bootstrap, PHP,
and MySQL. Include modules, normalized database tables, request flow, useful
libraries, and security controls for authentication, authorization, password storage,
SQL injection, XSS, CSRF, privacy, logging, and backups. Keep Version 1 small enough
for a student team. Explain where every security check is enforced.
```

**Why it worked:** The required stack and security topics prevented a generic cloud architecture answer. Asking where controls are enforced kept the answer practical.

### Prompt 5 - critical review

```text
Audit this CRM report against the assignment checklist. Identify missing questions,
unsupported facts, claims that may be outdated, places where commercial and
open-source editions are mixed together, and statements that sound like an install
was completed when it was not. Do not rewrite the report. Return a prioritized fix list.
```

**Why it worked:** It gave AI a reviewer role instead of asking for more content. The final sentence limited scope and produced a useful checklist.

### Prompt 6 - installation troubleshooting

```text
I am installing SuiteCRM 7.14.9 locally with XAMPP 8.2 on Windows for a short class
evaluation. Create a troubleshooting decision tree for Apache port conflicts, missing
PHP extensions, MariaDB connection errors, file-permission errors, and blank pages.
Use only fixes consistent with SuiteCRM's official compatibility matrix. Ask for the
exact error text before suggesting a destructive change.
```

**Why it worked:** The prompt supplied exact versions and required conservative troubleshooting. This is safer than asking “why doesn't it work?”

## AI effectiveness analysis

### What AI did well

AI was good at creating an outline, suggesting comparison fields, turning a long assignment into a checklist, and explaining unfamiliar terms in simple language. It also helped connect modules to database tables and identify security topics that belong in the architecture section.

### What AI struggled with

AI sometimes mixed editions and dates. For example, a product may be open source while advanced reporting is paid, or a vendor may change which PHP version the newest release supports. It also wanted to give exact subscription prices without a date or source. Broad questions produced polished answers that hid these differences.

### What information required validation

I validated:

- the exact assignment title, deliverable names, required screenshots, required architecture stack, README headings, and rubric;
- current product pricing models and edition names;
- Salesforce market-share claims;
- SuiteCRM, EspoCRM, and Odoo technology stacks and licenses;
- SuiteCRM and EspoCRM installation requirements;
- whether the free edition includes the reporting screen required by the assignment.

### Incorrect or incomplete AI-generated responses

The first open-source recommendation favored EspoCRM because its official Docker setup is easy. That answer was incomplete for this assignment because EspoCRM's full Reports feature is in the paid Advanced Pack. Since the assignment requires a Reports or Analytics screenshot, I switched the evaluation choice to SuiteCRM, which has a built-in Reports module.

The first XAMPP instructions also said to download the newest EspoCRM release. That would not work with the current public XAMPP package because EspoCRM 9.3 requires PHP 8.3 or newer while the current XAMPP Windows download provides PHP 8.2. I removed that route rather than hiding a version mismatch.

The first history answer said one person definitely invented the term CRM. SAP's history says it is unclear who coined it. I removed the unsupported attribution.

### What surprised me

The biggest surprise was how much “open source” still requires product research. The source code may be open, but installation, reporting, official support, or enterprise features can have separate limits. The easiest product to install was not automatically the easiest product for this assignment.

### What I would do differently next time

I would start by turning the rubric into a validation checklist. Then I would collect official sources before writing product comparisons. I would also ask AI to label every claim as stable, version-dependent, price-dependent, or opinion. That would make outdated details easier to catch.

### Would I trust AI for software research?

I would trust AI to help organize the research and generate questions, but not as the only source. It is useful for speed and coverage. It is not reliable enough for prices, versions, security requirements, feature availability, or licensing without checking original documentation. My rule would be: use AI to find what needs attention, then use primary sources to decide what is true.
