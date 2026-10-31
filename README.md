# Awesome-Revenue-Operations-Lifecycle-Management

# Top Revenue Operations & Lifecycle Management Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Revenue Recognition, Billing Lifecycle & Self-Hosted RevOps Intelligence*  
**Last updated: November 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Revenue Operations & Lifecycle Management**. These tools enable organizations to connect the dots between sales, finance, and customer success—automating revenue recognition, managing subscription lifecycles, and surfacing the intelligence needed to act on revenue signals across the entire customer journey.

**Examples** include HubSpot Revenue Hub, Clari, Gong, Chargebee RevRec, Maxio, Subskribe, Leapfin, Ordway, and Monetize360 (the category leaders).

**Open-source emphasis**: Revenue Operations & Lifecycle Management is a domain where open-source tooling is **genuinely emerging but fragmented across the lifecycle stages**. The strongest active projects are **Recurso** (a complete billing engine with double-entry ledger and ASC 606 revenue recognition built in) , **Autumn** (a Stripe layer for subscriptions, credits, and usage-based pricing) , and **B2B SaaS RevOps Intelligence** (an end-to-end data platform with dbt, Lightdash, and Reverse ETL to HubSpot) . For revenue recognition specifically, **eRev** provides a pure-Python ASC 606/IFRS 15 system , while **nexus-sales-operations** orchestrates order-to-cash with revenue recognition reserved for its enterprise tier . The critical caveat: **no open-source project matches the integrated lifecycle breadth** of Clari (pipeline-to-forecast) or Chargebee RevRec (billing-to-recognition-to-reporting)—you either assemble components or accept that the full RevOps loop requires stitching multiple tools together.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-products)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[HubSpot Revenue Hub](https://www.hubspot.com/)**  
  Unified revenue operations within HubSpot's ecosystem; connects marketing, sales, and service data with revenue reporting and forecasting.

- **[Clari](https://www.clari.com/)**  
  The benchmark for revenue intelligence; aggregates CRM, email, calendar, and call data to forecast revenue, identify pipeline risk, and surface deal insights.

- **[Gong](https://www.gong.io/)**  
  Conversation intelligence platform; records and analyzes sales calls to extract objections, buying signals, and coaching insights, then correlates them with deal outcomes.

- **[Chargebee RevRec](https://www.chargebee.com/)**  
  Revenue recognition module within Chargebee's subscription management platform; automates ASC 606/IFRS 15 compliance alongside billing.

- **[Maxio](https://www.maxio.com/)**  
  Financial operations platform for B2B SaaS combining subscription billing (Chargify) and revenue recognition (SaaSOptics).

- **[Subskribe](https://www.subskribe.com/)**  
  Unified quote-to-revenue platform for SaaS; combines CPQ, billing, and revenue recognition in one system.

- **[Leapfin](https://www.leapfin.com/)**  
  Revenue accounting automation platform; connects billing, ERP, and payment data to streamline the financial close and revenue recognition.

- **[Ordway](https://ordwaylabs.com/)**  
  Billing and revenue automation platform for subscription businesses; handles complex pricing, invoicing, and revenue recognition.

- **[Monetize360](https://www.monetize360.com/)**  
  Revenue and billing platform for subscription and usage-based businesses; focuses on agile monetization and revenue lifecycle management.

## Open-Source GitHub Projects

### Billing & Revenue Recognition Engines

- **[Recurso](https://github.com/recurso-dev/recurso)**  
  The most complete open-source **billing engine with built-in revenue recognition** (MIT, Go + PostgreSQL) . Features: **double-entry ledger** (Postgres authoritative, optional TigerBeetle mirror) with reconciled **ASC 606 revenue recognition**; subscriptions, invoicing, multi-currency payments (Stripe, Razorpay, GoCardless, Adyen); **8 usage aggregations and 7 charge models** with exact rational math; **smart dunning** with a bandit-retry engine and Collections operator layer; **India GST depth** (Place of Supply, HSN, TDS, IRN e-invoicing); self-serve importers from Stripe and Chargebee; accounting sync to QuickBooks, Xero, NetSuite, Tally, and HubSpot CRM; **MCP server** for agent-operable billing . `make demo` spins up the full stack with sample data. **Best for SaaS teams wanting a self-hosted billing engine that owns the ledger and revenue recognition**—but it is billing/revenue-focused, not a full pipeline intelligence platform.

- **[Autumn](https://github.com/useautumn/autumn)**  
  Open-source **Stripe layer for any pricing model** (subscriptions, credits, usage-based, custom plans) . Three API calls (`attach`, `check`, `track`) handle all billing logic: purchase flows, access checks, and usage events. Decouples billing from application logic so pricing changes do not require DB migrations or in-app flow rebuilds. **Best for teams wanting flexible pricing without rebuilding billing infrastructure**—but it is a billing layer, not a revenue recognition or RevOps intelligence platform.

- **[eRev](https://github.com/ChipmunkRPA/eRev)**  
  Open-source **pure Python revenue recognition system** for ASC 606 / IFRS 15 (free tier available) . Lightweight SQLite database with 13 operational buttons; Windows EFS encryption for data at rest; backup/restore/reset/append/purge operations; real-time activity tracking with timestamps; connects to PowerBI/Tableau/Alteryx for BI integration . **Best for accountants wanting a local, secure revenue recognition tool** without cloud dependency—but it is a recognition tool only, not a billing or RevOps platform.

### RevOps Intelligence & Data Pipelines

- **[B2B SaaS RevOps Intelligence Engine](https://github.com/farrux05-ai/b2b-saas-revops-intelligence)**  
  Enterprise-grade **data platform transforming the warehouse into a revenue center** . Features: **dlt ingestion** from PostHog, HubSpot, Stripe, and Zendesk into Snowflake; **dbt transformations** with 160 tests (schema, relationship, custom SQL assertions); **Elementary observability** with anomaly monitoring and Slack alerts; **Lightdash BI** with dashboards-as-code for Executive, Finance (MRR waterfall, NRR/GRR), CS (at-risk accounts), Sales (pipeline), and Product (PQL); **Slack AI agent** for plain-English queries ("How many at-risk accounts this week?"); **Reverse ETL** pushing computed signals back to HubSpot (health status, upsell readiness, ARR); **Dagster** orchestration running daily at 07:00 UTC; Terraform-managed Snowflake infrastructure . **Best for teams wanting a complete, production-grade RevOps data platform**—but it is infrastructure requiring Snowflake, dbt, and engineering resources.

- **[RevenueOS](https://github.com/unempyd/revenueos)**  
  Self-hosted, MIT-licensed **"connect your business" agent platform** that finds opportunities, executes approved revenue work, and measures outcomes . Workers discover and act on: inbox replies/bounces, documents (PDF/Word/Excel read locally), content opportunities (with WordPress publish), Hacker News threads, growth metrics (GitHub traffic, PyPI downloads), and site fixes (deploy and measure) . **Honest disclosure**: "RevenueOS has 0 customers and $0 in revenue"—it is an early-stage product with live-proven paths (site deploy, content deliverable, Stripe read, mailbox) but unproven Google Ads/Meta Ads integration . **Best for founders wanting an agentic revenue ops workflow**—but it is action-oriented rather than forecasting/billing-focused.

### Order-to-Cash & CPQ

- **[nexus-sales-operations](https://github.com/azaharizaman/nexus-sales-operations)**  
  Open-source **Order-to-Cash workflow orchestrator** (MIT) with **progressive disclosure by tier** . Tier 1 (SMB): Quote → Order, Direct Invoicing. Tier 2 (Mid): Credit Limit Check. Tier 3 (Enterprise): **Revenue Recognition**, Advanced Pricing, Approval Workflows, Full Audit Trail . Composer package with adapters for `Nexus\Sales` (orders/quotes) and `Nexus\Receivable` (invoicing/credit control). **Best for SMB-to-enterprise teams wanting a tiered O2C foundation**—but revenue recognition is enterprise-tier only and the package is early-stage.

- **SwiftCPQ** — Open-source, vendor-agnostic **proposal/CPQ tool** positioned as an accessible alternative to ConnectWise CPQ and Kaseya Quote Manager (Vue, updated April 2026) . **Best for teams wanting lightweight CPQ**—but it is quote-focused, not revenue lifecycle management.

### Additional Strong Open-Source Options

- **Kill Bill** — Mature open-source **subscription billing and payment platform** (Apache 2.0, in production since 2010) with subscriptions, usage billing, invoicing, payments, dunning, tax plugins, multi-tenancy, and audit logs . **Best for complete subscription billing**—but requires Java expertise and does not include revenue recognition or RevOps intelligence.
- **BasaltCRM** — Open-source **AI-native CRM** (MIT) with a full GTM pipeline (Campaigns → LeadGen → Accounts → Contacts → Leads → Opportunities → Quotes → Contracts → Invoices → Projects), AI Insights widget (revenue risk, data integrity, task velocity), and integrated billing (SURGE, Mercury Bank) . **Best for teams wanting CRM + revenue pipeline in one platform**—but it is CRM-centric, not a dedicated RevOps lifecycle tool.

**Frameworks for building custom systems**: For **billing with revenue recognition and ledger**, Recurso provides the most complete open-source foundation . For **flexible pricing without billing rebuilds**, Autumn . For **RevOps data intelligence with Reverse ETL**, the B2B SaaS RevOps Intelligence Engine . For **ASC 606 recognition only**, eRev . For **Order-to-Cash orchestration**, nexus-sales-operations . No single open-source project matches Clari's **pipeline-to-forecast intelligence** or Chargebee RevRec's **billing-to-recognition-to-reporting integration**—you either assemble components or accept that the full RevOps loop requires stitching multiple tools together.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Revenue operations platforms handling financial data and revenue recognition must comply with applicable accounting standards (ASC 606, IFRS 15), tax regulations, and internal controls; **self-hosted solutions place full responsibility for ledger integrity, revenue recognition accuracy, and audit trails on the operator**.
- **Open-source RevOps and lifecycle management is fragmented but genuinely emerging**—Recurso provides billing with built-in ASC 606 recognition and a double-entry ledger , Autumn provides flexible pricing infrastructure , and the B2B SaaS RevOps Intelligence Engine provides a complete data platform with Reverse ETL . However, **no open-source project matches Clari's pipeline intelligence or Chargebee RevRec's integrated billing-to-recognition workflow**—organizations requiring the full lifecycle should evaluate commercial platforms or plan for assembly.
- Verify license terms for commercial use; Recurso uses MIT , Autumn is open-source (check repository) , and eRev has a free tier with premium options .

---

**Made for RevOps leaders, finance engineers, and organizations building revenue lifecycle infrastructure.**  
Let's make revenue operations more open, but with clear eyes about the integration gaps that commercial platforms still fill.
