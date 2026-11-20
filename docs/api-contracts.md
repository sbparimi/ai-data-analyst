# API Contract Planning

Do not implement endpoints until the domain model and authorization design are approved. Use OpenAPI as the contract source of truth.

## Candidate resource groups

- `/v1/workspaces`
- `/v1/projects`
- `/v1/datasets`
- `/v1/datasets/{dataset_id}/versions`
- `/v1/datasets/{dataset_id}/profile-runs`
- `/v1/analysis-runs`
- `/v1/analysis-runs/{run_id}`
- `/v1/insights`
- `/v1/investigations`
- `/v1/conversations`
- `/v1/dashboards`
- `/v1/reports`
- `/v1/exports`
- `/v1/usage`

## API rules

- Version public APIs.
- Validate request and response schemas.
- Use pagination for collections.
- Use idempotency keys for retryable create operations.
- Return stable error codes and correlation IDs.
- Never expose internal stack traces or secrets.
- Enforce tenant authorization on every resource.
- Long-running tasks return job/run IDs and explicit states.
- Define cancellation, retry and timeout behavior.
- Document rate, payload and resource limits.
- Use generated client types where practical.

## Contract review checklist

- Is the resource tenant-scoped?
- Is the operation idempotent?
- What are authorization requirements?
- What are limits and validation errors?
- Is the operation synchronous or asynchronous?
- What is the retry/cancellation behavior?
- Does response expose sensitive information?
- Is provenance returned where required?
