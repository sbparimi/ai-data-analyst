---
name: plan-milestone
description: Use before implementing any milestone or multi-file feature. Produces a bounded, evidence-based plan and acceptance criteria.
---

# Plan a Milestone

1. Read root `AGENTS.md`, `PLANS.md`, relevant PRD sections and ADRs.
2. Inspect actual code, tests, dependency versions and repository status.
3. Identify the smallest vertical slice and affected modules.
4. Map requirements to implementation files and tests.
5. Identify data/security boundaries and failure paths.
6. List unknowns as `UNKNOWN`; never guess.
7. Verify external APIs against official current documentation.
8. Propose acceptance criteria with exact commands and observable outputs.
9. Identify owner approvals required.
10. Do not implement until the task explicitly authorizes implementation and required gates are approved.

Output: scope, non-scope, dependencies, design, risks, files, test plan, acceptance criteria and open decisions.
