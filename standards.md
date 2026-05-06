# Standards & API Reference

> Project: FP&A Platform · Generated: 2026-05-06

## Industry Standards & Specifications

### Financial Reporting Standards

**US GAAP (Generally Accepted Accounting Principles)**
- Maintained by: Financial Accounting Standards Board (FASB)
- URL: https://fasb.org
- All FP&A outputs must produce GAAP-compliant three-statement financials (P&L, balance sheet, cash flow). An FP&A platform targeting US companies must model accounts in accordance with FASB codification guidance, including ASC 230 (cash flow), ASC 280 (segment reporting), and ASC 350 (intangibles/goodwill).

**IFRS (International Financial Reporting Standards)**
- Maintained by: IFRS Foundation / IASB
- URL: https://www.ifrs.org/issued-standards/list-of-standards/
- The international equivalent of GAAP; required in 140+ jurisdictions. FP&A platforms serving multi-national companies must support IFRS-compliant chart-of-accounts mapping, particularly IAS 1 (financial statement presentation), IFRS 9 (financial instruments), and IFRS 16 (leases). EY's *International GAAP® 2026* is the definitive practitioner reference.

**IFRS S1 — General Sustainability Disclosure Requirements**
- Maintained by: IFRS Foundation / ISSB
- URL: https://www.ifrs.org/issued-standards/ifrs-sustainability-standards-navigator/ifrs-s1-general-requirements/
- Effective for reporting periods beginning on or after 1 January 2024. Requires disclosure of all financially material sustainability-related risks and opportunities. FP&A platforms increasingly need to support ESG scenario modelling alongside traditional financial planning as finance teams integrate sustainability into long-range plans.

**IFRS S2 — Climate-related Disclosures**
- Maintained by: IFRS Foundation / ISSB
- URL: https://www.ifrs.org/issued-standards/ifrs-sustainability-standards-navigator/ifrs-s2-climate-related-disclosures/
- Requires disclosure of governance, strategy, risk management, and metrics related to climate risk. December 2025 amendments target GHG emissions disclosure requirements. Enterprise FP&A platforms should provide climate scenario planning templates aligned to S2's four-pillar framework, especially for public company clients.

### Digital Reporting & Taxonomy Standards

**XBRL (eXtensible Business Reporting Language)**
- Maintained by: XBRL International; US taxonomy maintained by FASB / XBRL US
- URL: https://www.xbrl.org · https://xbrl.us/xbrl-taxonomy/2026-us-gaap/
- Machine-readable financial reporting standard used for all SEC public company filings. The 2026 FASB XBRL Taxonomy (GAAP Financial Reporting Taxonomy + SEC Reporting Taxonomy) was released December 15, 2025, and accepted by EDGAR from March 16, 2026. FP&A platforms targeting public companies must map plan and actuals data to XBRL taxonomy elements to support Inline XBRL export for regulatory filings.

**US GAAP 2026 XBRL Taxonomy**
- Maintained by: FASB / XBRL US
- URL: https://xbrl.us/xbrl-taxonomy/2026-us-gaap/ · https://www.sec.gov/newsroom/whats-new/2603-2026-xbrl-taxonomies-update
- The 2026 GRT incorporates updates for accounting standards published through 1 December 2025. The 2026 DEI taxonomy adds the NYSETX value (NYSE Texas) and the FFD taxonomy relocates four concepts. Platforms building XBRL export should track annual taxonomy refreshes, as EDGAR strongly encourages use of the most recent version.

**EDGAR XBRL Filing Specification**
- Maintained by: US Securities and Exchange Commission
- URL: https://www.sec.gov/files/edgar/filer-information/specifications/xbrl-guide.pdf (April 2026 edition)
- The SEC staff's authoritative guide covering Inline XBRL requirements, tagging rules, and acceptable filing formats. FP&A platforms generating outputs for SEC filers must comply with this specification.

### Date & Time Standards

**ISO 8601 — Date and Time Representations**
- Maintained by: International Organization for Standardization
- URL: https://www.iso.org/iso-8601-date-and-time-format.html · https://www.iso.org/standard/70907.html (ISO 8601-1:2019)
- Universal date/time standard used for financial period definitions. Duration notation (e.g., P1Y, P6M, P3M) eliminates ambiguity in XBRL period tagging and multi-jurisdiction planning calendars. All FP&A data APIs should represent reporting periods as ISO 8601 duration strings and timestamps in ISO 8601 extended format (e.g., `2026-03-31T23:59:59Z`).

### Data Model & Query Standards

**MDX (MultiDimensional Expressions)**
- Specification: ISO standard (non-proprietary, broad prior art)
- URL: https://learn.microsoft.com/en-us/analysis-services/multidimensional-models/mdx/mdx-query-the-basic-query
- The de facto query language for OLAP / MOLAP databases. Supported by Microsoft Analysis Services, Oracle Essbase, and IBM Cognos. MDX enables slice-and-dice queries across financial dimensions (account, cost centre, entity, time, scenario). FP&A planning engines built on multidimensional data models should expose an MDX-compatible query interface for compatibility with Excel PivotTables and enterprise BI tools.

**DAX (Data Analysis Expressions)**
- Specification: Microsoft / Tabular model standard
- URL: https://learn.microsoft.com/en-us/dax/
- The formula language for in-memory columnar models (Power BI, SSAS Tabular, Fabric). DAX has largely overtaken MDX for in-memory BI since 2014. An FP&A platform with a columnar storage engine (DuckDB, Apache Arrow) should support DAX-compatible expression evaluation or provide a DAX bridge layer for Power BI integration.

**OpenAPI Specification v3.1 / v3.2**
- Maintained by: OpenAPI Initiative (Linux Foundation)
- URL: https://spec.openapis.org/oas/v3.2.0.html · https://www.openapis.org/
- The vendor-neutral standard for describing REST APIs in YAML or JSON. As of 2026, enterprise buyers treat OpenAPI specs as mandatory deliverables alongside working integrations. All FP&A platform API endpoints should be described in a machine-readable OpenAPI 3.1+ specification to enable AI agent discovery, SDK auto-generation, and partner integration.

**JSON Schema (Draft 2020-12)**
- Maintained by: JSON Schema Organization
- URL: https://json-schema.org
- OpenAPI 3.1 is fully compatible with JSON Schema Draft 2020-12. FP&A data payloads (budget versions, driver hierarchies, dimension members, actuals rows) should be described using JSON Schema to enable client-side validation and code generation across languages.

### Security & Authentication Standards

**OAuth 2.0**
- Specification: RFC 6749 (IETF)
- URL: https://www.rfc-editor.org/rfc/rfc6749
- The standard authorization framework for delegated API access. Enterprise FP&A integrations (ERP connectors, HRIS connectors, bank feed APIs) must use OAuth 2.0 token exchange rather than credential sharing. The Authorization Code flow with PKCE is preferred for web-based integrations; Client Credentials for server-to-server data pipelines.

**OpenID Connect (OIDC) 1.0**
- Specification: OpenID Foundation
- URL: https://openid.net/connect/
- Identity layer on top of OAuth 2.0; the standard for enterprise SSO integration. Financial SaaS platforms targeting enterprise buyers must support OIDC for single sign-on via corporate identity providers (Okta, Azure AD, Ping Identity). Required by most enterprise procurement checklists.

**SCIM 2.0 (System for Cross-Domain Identity Management)**
- Specification: RFC 7642–7644 (IETF)
- URL: https://www.rfc-editor.org/rfc/rfc7643
- Standard for automated user provisioning and lifecycle management. Enterprise finance teams need automated user onboarding and offboarding (especially for budget owners and cost centre managers). SCIM 2.0 integration with identity providers removes manual access management overhead.

**SAML 2.0**
- Specification: OASIS
- URL: https://docs.oasis-open.org/security/saml/v2.0/
- XML-based SSO standard common in legacy enterprise environments. Many large-enterprise FP&A buyers mandate SAML 2.0 federation alongside OIDC. Required for Workday and SAP SuccessFactors ecosystem SSO integration.

### Compliance & Audit Frameworks

**SOC 2 Type II (AICPA Trust Services Criteria)**
- Maintained by: American Institute of Certified Public Accountants
- URL: https://www.aicpa.org/interestareas/frc/assuranceadvisoryservices/aicpasoc2report.html
- The de facto security audit standard for SaaS platforms handling financial data. Covers Security, Availability, Confidentiality, Processing Integrity, and Privacy trust service criteria. Enterprise finance buyers (CFOs, security teams) require SOC 2 Type II reports before approving FP&A platform procurement. Audit covers a 12-month period with typical cost of $20,000–$80,000.

**COSO ERM Framework (2017, updated 2026)**
- Maintained by: Committee of Sponsoring Organizations of the Treadway Commission
- URL: https://www.coso.org/erm-framework
- The reference framework for enterprise risk management and internal controls. FP&A scenario planning modules can align scenario categories (strategic, operational, reporting, compliance) to COSO ERM's five-component structure. February 2026 supplement addresses internal control over generative AI, directly relevant to AI-powered FP&A features.

**GDPR (General Data Protection Regulation)**
- Maintained by: European Data Protection Board
- URL: https://gdpr.eu
- Applies to any FP&A platform processing personal data of EU residents (employee compensation data, cost centre owner PII). Article 28 mandates Data Processing Agreements (DPAs) with all sub-processors. Requires data residency options, breach notification within 72 hours, and right-to-erasure workflows. UK GDPR applies separately post-Brexit.

### Model Context Protocol

**MCP (Model Context Protocol) — November 2025 Specification**
- Maintained by: Anthropic (open standard)
- URL: https://modelcontextprotocol.io/specification/2025-11-25
- Open standard for connecting AI agents to external data sources and tools. As of early 2026, 10,000+ public MCP servers are active with 164M+ monthly Python SDK downloads. An FP&A platform should expose an MCP server so AI agents (Claude, Copilot, custom LLMs) can query plan data, execute scenario branches, and retrieve variance explanations through a standardised tool interface without requiring bespoke API integrations.

---

## Similar Products — Developer Documentation & APIs

### Anaplan

- **Description:** Enterprise connected planning platform with the proprietary Hyperblock multidimensional calculation engine. Market-leading for large-enterprise FP&A, supply chain, and workforce planning.
- **API Documentation:** https://help.anaplan.com/anaplan-api-844c6d40-a21c-423d-8435-ebaaa0372b76
- **Apiary Reference (Integration API v2.0):** https://anaplan.docs.apiary.io/ · https://anaplanbulkapi20.docs.apiary.io
- **SDKs/Libraries:** Java client — https://github.com/anaplaninc/anaplan-java-client; Python via dltHub — https://dlthub.com/context/source/anaplan
- **Developer Guide:** https://www.anaplan.com/resources/datasheets/anaplan-api-for-data-integrations/
- **Standards:** REST/JSON; Integration API v2.0; bulk API and transactional API endpoints; CloudWorks integration layer
- **Authentication:** Bearer token via Anaplan auth endpoint (Basic Auth to obtain token); supports OAuth 2.0 for production integrations

### Workday Adaptive Planning

- **Description:** Cloud-native FP&A platform deeply integrated with Workday HCM and Financials; targets mid-market to enterprise; strong workforce planning and three-statement modelling.
- **API Documentation:** https://doc.workday.com/adaptive-planning/en-us/workday-adaptive-planning-documentation/integration/managing-data-integration/api-documentation/understanding-the-adaptive-planning-rest-api/vmo1623708512342.html
- **API Methods Reference:** https://doc.workday.com/adaptive-planning/en-us/integration/managing-data-integration/api-documentation/understanding-the-adaptive-planning-rest-api/api-methods/brk1623709249507.html
- **SDKs/Libraries:** R package (community) — https://github.com/elipousson/adaptiveapi
- **Developer Guide:** https://revelwood.com/unlocking-workday-adaptive-plannings-power-with-its-apis/
- **Standards:** REST/JSON with both XML and JSON API variants; Workday credential-based JWT Bearer auth (AdaptiveAPIAccessToken)
- **Authentication:** AdaptiveAPIAccessToken (JWT Bearer); Workday SSO credential federation for enterprise deployments

### Pigment

- **Description:** Modern multi-dimensional FP&A platform with AI agent layer (Analyst, Planner, Modeler); 200+ pre-built integrations; targets mid-market to enterprise with real-time collaborative modelling.
- **API Documentation:** https://kb.pigment.com/docs/rest-client-sample-api-requests · https://pigment.app/api/swagger (Swagger/OpenAPI spec)
- **Export API Guide:** https://kb.pigment.com/docs/export-data-with-apis
- **Metadata API:** https://kb.pigment.com/docs/retrieve-info-metadata-api
- **SDKs/Libraries:** Available via Celigo connector — https://docs.celigo.com/hc/en-us/articles/24075884725915-Available-Pigment-APIs
- **Developer Guide:** https://kb.pigment.com/
- **Standards:** REST/JSON; OpenAPI (Swagger) spec available; rate limit of 500 requests per 5-minute window per IP
- **Authentication:** API key (Export API key per integration)

### Planful

- **Description:** Mid-market FP&A with structured planning, dynamic planning, consolidation, and reporting modules. Strong financial consolidation and management reporting capabilities.
- **API Documentation:** https://developers.planful.com/ · https://help.planful.com/docs/api-library-structured-planning-consolidation-reporting-analytics
- **REST API (v2):** https://help.planful.com/v2/docs/introduction
- **Transfer Data API:** https://help.planful.com/docs/new-transfer-data-rest-api
- **Dynamic Planning API:** https://help.planful.com/v1/docs/dynamic-planning-api-library
- **SDKs/Libraries:** No official SDK; community integrations via Tray.ai and Boomi
- **Standards:** REST/JSON (primary) and SOAP (legacy); POST and PUT methods for data transfer; 200 OK (sync) / 202 Accepted (async) responses
- **Authentication:** Token-based (Login API returns session token); HTTPS required

### Vena Solutions

- **Description:** Excel-native FP&A platform that combines managed Excel grids with a centralised data model; strong budgeting, consolidation, and governance for finance teams that want to preserve Excel workflows.
- **API Documentation:** https://developers.venasolutions.com/
- **Load Data Guide:** https://developers.venasolutions.com/docs/load-data-into-vena
- **Auth Reference:** https://developers.venasolutions.com/reference/authorization-and-authentication
- **Microsoft Power Automate Connector:** https://learn.microsoft.com/en-us/connectors/vena/
- **SDKs/Libraries:** Python library for ETL automation (referenced in developer portal); GitHub — https://github.com/venasolutions
- **Standards:** REST/JSON; Import and Export APIs; JSON and CSV data upload support
- **Authentication:** HTTP Basic Auth with Application Tokens (generated in Vena Admin → Application Tokens); all requests over HTTPS

### Datarails

- **Description:** Excel-native FP&A with AI-powered financial narrative generation; targets SMB and mid-market finance teams of 2–10 people; three AI agents (Strategy, Reporting, Planning).
- **API Documentation:** https://support.datarails.com/hc/en-us/articles/14616773038620-Data-Gateway-Service-DGS-API-Documentation
- **Integration Methods:** https://support.datarails.com/hc/en-us/articles/10601349650973-Integration-Methods
- **Community SDK (Python, unofficial):** https://jessemaitland.github.io/datarails/
- **Standards:** REST/JSON; file upload via multipart form (CSV / XLSX); DGS API endpoint at `https://app.datarails.com/api/v1/fileboxes/upload_file`
- **Authentication:** Basic Auth (Base64-encoded credentials in Authorization header)

### Mosaic Tech / HiBob

- **Description:** Mosaic was acquired by HiBob in 2025; now provides integrated workforce-and-finance planning combining SaaS metrics intelligence with HiBob HRIS data. Conversational AI for ad-hoc financial queries.
- **HiBob API Documentation:** https://apidocs.hibob.com/
- **Getting Started:** https://apidocs.hibob.com/docs/getting-started
- **API Reference:** https://apidocs.hibob.com/reference/getting-started-with-bob-api
- **Mosaic API Tracker:** https://apitracker.io/a/mosaic-tech
- **Standards:** REST/JSON; base URL `https://api.hibob.com/v1`; cursor-based pagination (up to 1000 records per page); rate limits enforced per Service User
- **Authentication:** HTTP Basic Auth with Base64-encoded Service User ID and token (serviceUserId:serviceUserToken)

### Cube (cube.fm)

- **Description:** Spreadsheet-native FP&A that syncs with Google Sheets and Excel; also refers to Cube.dev, the open-source semantic layer project. API-first architecture with REST, GraphQL, and SQL interfaces.
- **FP&A Developer Center:** https://www.cubesoftware.com/developer-center
- **Cube.dev REST API:** https://cube.dev/docs/product/apis-integrations/rest-api · https://cube.dev/docs/reference/rest-api
- **MDX API (Excel integration):** https://cube.dev/blog/announcing-the-native-mdx-api-and-excel-integration-for-cube-cloud
- **GraphQL API:** https://cube.dev/docs/product/apis-integrations
- **SDKs/Libraries:** JavaScript SDK (cubeapi npm package); REST, GraphQL, and SQL APIs available natively
- **Standards:** REST/JSON; GraphQL; SQL; MDX (native MDX API for Excel); OpenAPI spec available (`openspec.yml`); base path `/cubejs-api`
- **Authentication:** API scopes and CORS; JWT-based tokens; WebSocket transport supported via CubeApi constructor

---

## Notes

**Jirav:** Jirav (https://www.jirav.com) does not appear to publish a public developer API or an integration documentation portal as of May 2026. Integration is primarily handled through pre-built connectors to QuickBooks, Xero, NetSuite, and HRIS platforms. Developers requiring custom integrations should contact Jirav directly.

**Abacum:** Abacum (https://www.abacum.ai) similarly does not surface a public API documentation portal. Custom integrations are handled via their data connectors layer. Abacum's REST API, if accessible, requires a partner agreement.

**Emerging Standard — Agent-to-Agent (A2A) Protocol:** The A2A protocol (a2a-mcp.org) is an emerging complement to MCP for multi-agent financial workflows. As FP&A platforms adopt agentic architectures (Pigment's Analyst/Planner/Modeler agents, Mosaic's conversational AI), inter-agent communication standards will become relevant for coordinating scenario generation, variance analysis, and model maintenance agents.

**Open Finance / Berlin Group:** The Berlin Group's openFinance API Framework (https://www.berlin-group.org/open-finance) provides a harmonised set of open banking APIs for secure financial data sharing. FP&A platforms integrating bank feed actuals for 13-week cash flow forecasting should evaluate PSD2/openFinance-compliant data providers rather than direct screen-scraping.
