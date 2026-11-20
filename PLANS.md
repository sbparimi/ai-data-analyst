# Development Roadmap

This roadmap is a proposed sequence. Codex must refine estimates and dependencies after inspecting the repository and verifying current technology choices. Do not invent delivery dates.

## Stage 0 — Discovery and engineering foundation (M0)
Deliverables:
- Approved PRD, architecture, threat model, data model, API contracts, ADRs.
- Repository layout, local development setup, lint/type/test commands.
- CI checks and contribution workflow.
- Dependency and license policy.
Exit gate: reproducible clean setup; CI green; architecture decisions reviewed.

## Stage 1 — SaaS foundation (M1)
Deliverables:
- Authentication adapter and user/workspace/project domain.
- Tenant-scoped authorization and persistence.
- Audit events and ownership tests.
- Local development identity strategy; no real account connection without approval.
Exit gate: cross-tenant access tests prove isolation for all resource types.

## Stage 2 — Ingestion and profiling (M2-M3)
Deliverables:
- Secure XLSX/CSV ingestion.
- Content-based file validation, resource limits, safe parsing.
- Immutable source artifact and versioned dataset metadata.
- Schema inference, profiling, quality findings, preview.
Exit gate: golden ingestion fixtures and malicious-file tests pass.

## Stage 3 — Deterministic analytics (M4)
Deliverables:
- Metric definition registry.
- Typed analytical operations.
- Aggregations, distributions, time trends, segment comparisons, correlations where valid.
- Bounded anomaly detection with documented method and caveats.
- Reproducible evidence records.
Exit gate: calculations match independently generated expected results across edge cases.

## Stage 4 — Insights and diagnostic investigations (M5-M6)
Deliverables:
- Insight schema and prioritization rules.
- Evidence-linked narrative generation.
- Supported driver decomposition and contribution analysis.
- Validation/abstention layer.
Exit gate: no unsupported insight reaches the UI; evaluation fixtures pass.

## Stage 5 — Conversational analyst (M7)
Deliverables:
- Natural-language intent parsing.
- Tool selection from an allowlisted analytical tool registry.
- Query planning, validation, bounded execution and provenance.
- Clarification and abstention behavior.
Exit gate: benchmark questions produce correct answers and safe failure modes.

## Stage 6 — Dashboards and reports (M8, M10)
Deliverables:
- Dashboard schema based on validated result IDs.
- Interactive filters and drilldowns.
- Accessible charts and table views.
- Exportable report with dataset version, definitions, caveats and evidence.
Exit gate: visual E2E and report-to-source consistency tests pass.

## Stage 7 — Forecasting and recommendations (M9)
Deliverables:
- Forecasting only for supported time-series shapes.
- Backtesting, baseline comparison, uncertainty intervals.
- Recommendation templates with explicit assumptions and impact calculations.
Exit gate: forecasts beat or appropriately abstain against baseline evaluation; no causal claims without causal design.

## Stage 8 — Commercial SaaS (M11)
Deliverables:
- Plan/entitlement model, metering, quotas and billing adapter.
- Admin and support controls.
- Usage transparency and cancellation/data deletion flows.
Exit gate: entitlement, billing webhook, idempotency and abuse tests pass. Payment provider choice requires ADR and approval.

## Stage 9 — Production readiness (M12)
Deliverables:
- Threat-model closure, dependency scanning, observability, SLO proposals.
- Load and resilience testing.
- Backup/restore and retention verification.
- Infrastructure as code and deployment runbooks.
- Human-approved production release.
Exit gate: signed release checklist and explicit production approval.

## Dependency rule

Do not start a downstream milestone if its upstream contracts are unstable. Parallelize only isolated work with agreed contracts and an integration owner.

## Status tracking

Use `harness/milestone-status.md`. A milestone may be marked COMPLETE only with commit references, test commands, results, and reviewer acceptance.
