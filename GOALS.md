# Product Goals and Non-Goals

## Vision

An autonomous business intelligence analyst for non-specialist users. A user uploads a spreadsheet or connects an approved source; the platform profiles the data, discovers relevant metrics, performs validated analysis, investigates material changes, and communicates evidence-backed findings and actions.

## Primary users

- Small and medium business owners
- Finance and operations managers
- E-commerce operators
- Sales and marketing managers
- Analysts who need faster exploratory work

These are target segments, not validated customer demand. Validate with interviews and usage research before committing to vertical-specific features.

## User outcomes

1. Understand what a dataset contains without manual schema documentation.
2. Identify data quality issues and analytical limitations.
3. Discover relevant descriptive metrics and trends.
4. Investigate material changes and segment contributions.
5. Ask natural-language questions and receive reproducible answers.
6. Explore findings in interactive dashboards.
7. Evaluate forecasts with transparent uncertainty.
8. Receive recommendations with evidence and explicit assumptions.
9. Export a traceable management report.

## Product principles

- Evidence before explanation.
- Deterministic computation before generative interpretation.
- Abstention over unsupported certainty.
- Transparent assumptions and uncertainty.
- User control over data and transformations.
- Secure tenant isolation by design.
- Accessible, understandable interfaces.
- Incremental delivery with measurable acceptance criteria.

## Non-goals for initial MVP

- Replacing a full enterprise data warehouse or BI suite.
- Arbitrary code execution on uploaded files.
- Autonomous write access to external business systems.
- Automated financial, legal, medical, or investment advice.
- Guaranteeing causal inference from observational data.
- Supporting every file format or connector at launch.
- Multi-agent complexity without demonstrated need.
- Real-time streaming analytics in the first release.
- Training foundation models on customer uploads.

## MVP scope

- Multi-tenant user/workspace/project foundation.
- XLSX and CSV upload with strict limits.
- Dataset profiling and data-quality report.
- Deterministic descriptive analytics and metric discovery.
- Evidence-backed insight generation.
- A bounded root-cause/driver decomposition for supported metrics.
- Conversational Q&A over approved analytical tools.
- Interactive dashboard from validated result objects.
- Exportable report.
- Synthetic golden datasets and evaluation harness.

## Product success criteria

Set numeric targets only after baseline measurement and product validation. Initial release gates should focus on correctness, reproducibility, security, usability, and end-to-end completion rather than invented growth targets.
