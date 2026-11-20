# Product Requirements Document

## 1. Problem

Spreadsheet users often have data but lack the time or expertise to profile it, identify meaningful metrics, investigate changes, and turn analysis into decisions. Generic chat interfaces can produce plausible but unverifiable answers.

## 2. Proposed solution

A SaaS analyst that combines deterministic data processing with AI-assisted planning and explanation. It must preserve provenance from source file through profile, metric, analysis, insight, chart, and report.

## 3. Core user journey

1. User creates a workspace and project.
2. User uploads XLSX or CSV.
3. System validates file safety and resource bounds.
4. System stores an immutable source artifact and creates a dataset version.
5. Parser extracts sheets/tables into a controlled analytical representation.
6. Profiler identifies schema, types, missingness, uniqueness, distributions and likely semantic roles.
7. System presents data quality issues and asks for clarification where ambiguity affects results.
8. Deterministic engine calculates supported metrics and analysis.
9. Insight service ranks findings using transparent rules.
10. AI explains only validated findings and may request additional approved analysis.
11. User explores dashboard and asks questions.
12. User exports a traceable report.

## 4. Functional requirements

### FR-01 Identity and tenancy
- Users belong to workspaces through explicit memberships and roles.
- Every project, dataset, run, insight, dashboard and export has tenant ownership.
- Authorization is enforced server-side on every operation.

### FR-02 Upload
- MVP formats: CSV and XLSX.
- Validate actual file content, size, extension, encoding, sheet count, dimensions and parser behavior.
- Reject unsupported, encrypted, malformed, macro-enabled or resource-exhausting inputs unless explicitly supported by a reviewed safe parser.
- Never execute spreadsheet formulas or macros.
- Preserve original file as immutable source artifact.

### FR-03 Profiling
- Infer column types with confidence and record ambiguity.
- Compute row/column counts, null counts, distinct counts, duplicate candidates, distributions and outliers.
- Identify likely dates, measures, dimensions and identifiers without treating inference as certainty.
- Explain limitations.

### FR-04 Analytics
- Support typed, allowlisted operations.
- Every operation declares input dataset version, filters, grouping dimensions, time grain, null handling, units and calculation method.
- Return structured results and provenance.
- Reject invalid statistical assumptions or insufficient sample sizes.

### FR-05 Insights
- Insight includes title, description, type, severity/priority, evidence references, method, assumptions, confidence/limitations and suggested follow-up.
- Never infer causality from correlation or decomposition alone.
- Suppress unsupported claims.

### FR-06 Diagnostic investigation
- Decompose supported aggregate changes by available dimensions.
- Show contribution and residual/unexplained portions.
- Clearly label associations and contributions, not causal causes.
- Require sufficient comparable periods and consistent metric definitions.

### FR-07 Conversational Q&A
- Translate questions into an internal plan using an allowlisted tool registry.
- Validate all arguments and query plans.
- Execute read-only operations under limits.
- Show calculation and source provenance.
- Ask clarifying questions or abstain when ambiguous.

### FR-08 Dashboards
- Dashboard components reference validated result IDs and schemas.
- Charts must not contain model-invented values.
- Filters must preserve metric definitions and authorization scope.
- Accessibility and empty/error states are required.

### FR-09 Reports
- Include data source/version, analysis timestamp, metric definitions, assumptions, limitations and evidence.
- Exported figures must match dashboard results.
- Support PDF and XLSX only after a secure implementation is tested.

### FR-10 Auditability
- Record actor, action, resource ID, tenant ID, timestamp and outcome.
- Avoid logging raw sensitive cell values or secrets.

## 5. Non-functional requirements

- Security: threat-modelled, tenant isolated, least privilege.
- Reliability: long-running analysis is asynchronous and resumable.
- Performance: limits and budgets are configurable; establish measured baselines.
- Observability: structured logs, traces and metrics without sensitive payloads.
- Accessibility: target WCAG 2.2 AA; validate with automated and manual checks.
- Maintainability: typed boundaries, modular domain code, ADRs.
- Portability: local Docker development; cloud adapters behind interfaces.

## 6. Open product questions

Codex must not silently decide these. Create ADRs or request owner input:
- Initial deployment region and data residency.
- Authentication provider.
- LLM provider/model and data-processing terms.
- Maximum upload size, rows, columns and runtime budgets.
- Retention and deletion policy.
- Billing provider and initial plan limits.
- Whether users can connect external data sources in MVP.
- Supported languages, currencies, time zones and fiscal calendars.
