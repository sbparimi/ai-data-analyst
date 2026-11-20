---
name: quality-gates
description: Use before marking work complete, opening a PR, merging or recommending release.
---

# Quality Gates

- Map each acceptance criterion to test evidence.
- Run relevant unit, integration, API, E2E, security and static checks.
- Record exact command, commit, exit code, environment and result.
- Review the full diff for unrelated changes, secrets and unsafe operations.
- Do not alter tests to conceal defects.
- Report skipped tests and environmental limitations.
- A milestone is not complete while critical acceptance criteria are unverified.
- Production deployment and release require explicit human approval.
