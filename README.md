# FP&A Platform

> Part of the [worlds-biggest-software-project](https://github.com/worlds-biggest-software-project) initiative.
>
> An open-source, AI-native financial planning and analysis platform for driver-based modelling, budgeting, and scenario planning.

FP&A Platform is a multi-dimensional planning engine for finance teams who need to model business drivers, run scenarios, and reforecast continuously without paying six-figure contracts to incumbent vendors. It is aimed at mid-market CFOs, enterprise FP&A leaders, and SaaS finance teams who want transparent, auditable models instead of black-box proprietary tools. The project addresses a market that today has no viable open-source alternative.

---

## Why FP&A Platform?

- Every established FP&A tool — Anaplan, Workday Adaptive, Planful, Vena, Pigment — is fully proprietary, with no viable open-source planning engine in the category.
- Pricing locks out a large underserved segment: minimum viable Anaplan implementations exceed $100K/year, Planful starts at ~$32K/year, and most platforms require multi-month sales cycles before disclosing a quote.
- Companies between $5M–$50M revenue cannot justify these contracts and are forced to remain on Excel-based management packs that lack governance, version control, and audit trails.
- Existing AI features sit inside opaque commercial platforms; finance and audit functions need transparent, inspectable driver logic with version-controlled change history before they can adopt AI in regulated environments.
- Anaplan's Hyperblock architecture is proprietary, but the underlying multi-dimensional MOLAP techniques, driver-based modelling, and three-statement financial modelling are standard, non-patented approaches — making an OSS engine viable.

---

## Key Features

### Planning Engine and Financial Model

- Multi-dimensional planning engine with driver-based modelling and formula evaluation
- Three-statement financial model (P&L, balance sheet, cash flow) with automatic linkage
- Rolling forecast automation with configurable time horizons
- Scenario management with at least three concurrent plan versions and side-by-side variance comparison
- Workforce and headcount planning with compensation roll-up to P&L

### Consolidation, Actuals, and Workflow

- Multi-entity consolidation with currency translation and intercompany eliminations
- ERP and accounting integration for automated actuals loading (QuickBooks, Xero, NetSuite at minimum)
- Continuous actuals sync with intra-month reforecast recalibration
- Role-based access for budget owners, FP&A analysts, CFOs, and read-only stakeholders
- Approval workflows for budget submission and reforecast sign-off

### AI Agents and Natural-Language Interface

- Natural-language query interface for ad-hoc variance and forecast questions
- AI-generated variance commentary for management reporting and board packs
- Conversational scenario generation that turns plain-English prompts into multi-dimensional plan branches
- Automated driver discovery surfacing statistical correlations between operational metrics and financial outcomes
- Anomaly detection on actuals to flag unexpected transactions or coding errors before period close

### SaaS and Specialised Modules

- SaaS metrics module covering ARR, MRR, NRR, churn, CAC, and LTV cohort analysis
- 13-week cash flow forecasting with bank feed integration
- Board pack export templates with auto-populated charts and commentary
- XBRL export for public company regulatory submissions

---

## AI-Native Advantage

Incumbent platforms bolt AI onto proprietary engines users cannot inspect. This project is designed AI-native around four capabilities the source research identifies as genuinely differentiating: automated driver discovery that proposes and validates correlations between operational and financial data, natural-language scenario generation that lowers the skill barrier for non-finance stakeholders, continuous forecast recalibration from live ERP and billing feeds rather than monthly batch cycles, and explainable AI guardrails with transparent driver logic and version-controlled model history suitable for audit and regulated finance environments.

---

## Tech Stack & Deployment

The platform is intended to ship as an open-source core with an optional hosted cloud tier, supporting both self-hosted and managed deployments. The planning engine is built on standard multi-dimensional data modelling techniques — OLAP cubes, columnar storage, and DAG-based dependency resolution — with no identified IP risk. Outputs are mappable to XBRL taxonomies for SEC and regulatory submissions, and produce GAAP- and IFRS-compliant financial statements. Integration follows the de facto REST + JSON pattern, with pre-built connectors planned for the major ERP, HRIS, and accounting systems referenced in the source research.

---

## Market Context

The global FP&A software market was valued at approximately $5.82B in 2024 and is projected to reach $13.91B by 2033 at a CAGR of ~10.2% (Data Insights Market). Cloud-based FP&A for public companies is projected at ~$8.5B in 2026 growing at 28% CAGR (MGI Research), with the AI-powered FP&A segment growing 16–18% annually through 2034. Primary buyers are mid-market CFOs replacing Excel, enterprise FP&A directors needing multi-entity consolidation, SaaS finance leaders requiring ARR and cohort metrics, and startup CFOs graduating from spreadsheets — segments currently paying $24K to $1M+ per year to proprietary vendors.

---

## Project Status

> This project is in the **research and specification phase**.  
> Contributions, feedback, and domain expertise are welcome.

---

## Contributing

We welcome contributions from developers, domain experts, and potential users.
See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Important:** All contributions must be your own original work or clearly attributed
open-source material with a compatible licence. Copyright infringement and licence
violations will not be tolerated and will result in immediate removal of the offending
contribution. If you are unsure whether a piece of code, text, or other material is
safe to contribute, open an issue and ask before submitting.

---

## Licence

Licence to be determined. See [discussion](#) for context.
