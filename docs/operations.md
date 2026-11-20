# Operations and Production Readiness

## Environments

- Local: Docker Compose with synthetic data and local service emulators.
- CI: ephemeral isolated environment.
- Staging: production-like, synthetic or approved masked data.
- Production: separate accounts/projects, least privilege and explicit approval.

## Observability

Capture:
- request/job correlation IDs
- job lifecycle and duration
- ingestion/parser failures
- analytical operation failures
- model latency/token/cost metadata where available
- validation/abstention rates
- queue depth and worker saturation
- resource usage
- tenant-safe usage counters

Do not log raw dataset cells, prompts containing sensitive values, secrets, or full model payloads by default.

## Resilience

- Idempotent job processing.
- Retry only transient failures with bounded backoff.
- Dead-letter or failed-job inspection.
- Cancellation and timeout handling.
- Checkpoint long workflows where justified.
- Object and metadata consistency checks.
- Backup/restore drills.

## Cost controls

- Enforce upload and compute quotas.
- Bound model context and output.
- Cache only with tenant-safe keys and correct invalidation.
- Track cost per analysis run.
- Avoid agent loops; impose step, token, time and tool-call budgets.
- Require approval for paid cloud provisioning and production spend.

## Release checklist

See `harness/release-checklist.md`. Production release is always human-approved.
