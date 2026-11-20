# Autonomous AI Data Analyst

A Codex-first blueprint for a multi-tenant SaaS that turns uploaded business data into reproducible analysis, evidence-backed insights, diagnostics, dashboards, forecasts, recommendations and management reports.

## Status

Planning baseline only. This repository does not yet contain the application implementation. The documents define product intent, engineering constraints, architecture boundaries, milestones, agent roles, Codex skills, testing standards and release gates.

## Start with Codex

1. Read `AGENTS.md`, `GOALS.md`, `PLANS.md`, all relevant files under `docs/`, and the skills under `.agents/skills/`.
2. Follow `docs/codex/BOOTSTRAP_TASK.md` in Plan mode.
3. Inspect the actual repository and verify technology choices against current official documentation.
4. Produce the required reviews and ADRs. Stop for human review before implementing application features.

## Product promise

Upload business data. Discover what happened, investigate why, understand what may happen next, and identify actions justified by evidence.

## Critical trust rule

The LLM is not the calculator, database, source of truth or validator. Deterministic code executes calculations. AI may plan, select approved analytical operations, interpret validated results and explain them. Unsupported findings must be withheld.

## Repository map

- `AGENTS.md` — mandatory repository-wide Codex instructions.
- `GOALS.md` — product goals and non-goals.
- `PLANS.md` — staged implementation roadmap and dependencies.
- `docs/` — requirements, architecture, security, data, analytics, API, evaluation, operations and decisions.
- `.agents/skills/` — task-specific Codex skills.
- `agents/` — specialist engineering role contracts.
- `harness/` — milestone status, build evidence and release checklist.
- `.github/` — issue and pull-request templates.

## Implementation status

No application features are implemented by this planning baseline. M0 is the first engineering milestone. Mark work complete only with commit references, test evidence and reviewer acceptance.
