# Codex Bootstrap Task — Planning Only

Read, in order:
1. `/AGENTS.md`
2. `/GOALS.md`
3. `/PLANS.md`
4. All relevant files under `/docs/`
5. All relevant skills under `/.agents/skills/`

Then inspect the actual repository, available runtimes, package managers, existing code and CI environment.

Produce:
- `docs/reviews/initial-repository-assessment.md`
- `docs/reviews/architecture-review.md`
- `docs/reviews/threat-model-review.md`
- `docs/reviews/technology-verification.md`
- `docs/reviews/milestone-plan.md`
- ADRs for every material technology choice.

For every external SDK/framework decision:
- Verify current official documentation and package version.
- Record the source URL, access date and verified API behavior.
- Do not rely on remembered APIs or fabricated examples.

Challenge the proposed architecture. In particular assess whether PostgreSQL, object storage, DuckDB/Polars, a queue, Temporal, pgvector, Redis and the selected AI SDK are justified for the MVP. Remove unnecessary components through ADRs rather than accepting every suggestion.

Define:
- domain boundaries
- tenancy and authorization
- upload security
- data lineage and evidence schema
- deterministic analytics contracts
- AI tool allowlist and sandbox boundaries
- testing and evaluation design
- local developer workflow
- CI quality gates
- operational cost risks

Do not create application features, connect accounts, provision cloud resources, install paid services, or deploy anything in this task.

End with:
1. Decisions requiring product-owner approval.
2. Risks ranked by severity.
3. Exact next implementation task for M0.
4. Acceptance criteria and commands to verify M0.

Stop and wait for human review.
