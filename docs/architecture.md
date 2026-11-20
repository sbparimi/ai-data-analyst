# Proposed Architecture

## Architectural style

Start with a modular monolith plus asynchronous workers. Split services only when measured scaling, isolation, or team ownership justifies it.

## Logical components

1. Web application: user experience, upload, dataset exploration, chat, dashboards and reports.
2. API layer: authentication context, authorization, validation and domain commands.
3. Domain modules: workspace, project, dataset, ingestion, profiling, analytics, evidence, insights, investigation, conversation, dashboard, report and audit.
4. Analytical runtime: isolated, resource-limited processing of parsed data using DuckDB/Polars where benchmarked and justified.
5. AI adapter/orchestrator: provider-neutral interface; model proposes plans and explains validated results.
6. Worker system: long-running ingestion, analysis, forecast and export jobs.
7. Persistence: relational metadata, object storage for source and derived artifacts, optional vector search only after a concrete retrieval requirement.

## Data flow

Upload -> quarantine/validation -> immutable source artifact -> parse -> dataset version -> profile -> deterministic analysis -> evidence objects -> insight validation -> AI narrative -> dashboard/report.

## Trust boundaries

- Browser to API.
- API to object storage.
- API to worker queue.
- Worker to parser/analytical runtime.
- Orchestrator to model provider.
- Analytical runtime to database.
- Tenant A to Tenant B.
- User-supplied file content to system instructions.

## Core boundaries

- Domain logic must not import web framework or provider SDK types.
- Analytics engine accepts typed data references and operation specs, not arbitrary model-generated code.
- AI layer can call only registered tools.
- Evidence store is append-only/versioned for a completed analysis run.
- Dashboard and report renderers consume validated result schemas only.

## Proposed stack (subject to ADR verification)

- Web: Next.js, React, TypeScript.
- API: FastAPI, Python.
- Data: Polars and DuckDB; Pandas only where required by ecosystem compatibility.
- Metadata: PostgreSQL.
- Object storage: S3-compatible interface; local emulator for development.
- Queue/workflows: begin with a managed/simple queue unless durable multi-step orchestration is justified; evaluate Temporal via ADR.
- Charts: choose an accessible React charting library after prototype and license review.
- AI: provider adapter; evaluate OpenAI Agents SDK only after verifying current official docs, package version, data handling and tool safety.
- Infra: Docker for local development; Terraform only when cloud architecture is approved.

## Decisions not to assume

- Do not assume pgvector is required. Add only for semantic retrieval with a measured use case.
- Do not assume Redis is required. Add only for a concrete cache/queue/coordination need.
- Do not assume Temporal is required for the MVP.
- Do not assume all uploaded formats are safe or supported.
- Do not assume a model provider can process customer data under acceptable terms.
