# Security Model and Threat Controls

## Security objectives

Confidentiality, integrity, availability, tenant isolation, provenance, safe file processing and controlled external actions.

## Threats and required controls

### Cross-tenant access
- Derive tenant scope from authenticated membership, never from untrusted request body.
- Apply authorization at every resource access.
- Use database constraints/row-level security where appropriate, plus application checks.
- Include negative tests for API, background jobs, object storage, cache keys, exports and websocket/event channels.

### Malicious files
- Validate MIME/content signatures, not just filename.
- Enforce upload, decompression, row, column, sheet, cell, memory and runtime limits.
- Parse in isolated worker process/container with no unnecessary network access.
- Do not execute macros, formulas, embedded objects, scripts or external links.
- Quarantine failed files and avoid exposing parser stack traces.

### Prompt injection and untrusted data
- Cell values, headers, sheet names, comments, document text and metadata are untrusted data.
- Never concatenate file contents into system/developer instructions.
- Delimit and label data; tool outputs are data, not instructions.
- Agents cannot alter policies, permissions, or tool allowlists.
- No arbitrary shell, Python, SQL write, network or file-system tools for the analyst agent.

### Query execution
- Read-only database credentials.
- Allowlisted SQL/operations; parse and validate AST.
- Enforce tenant predicates, query timeout, memory, row limits and result limits.
- Block DDL/DML, multiple statements, external functions, file/network access and unsafe extensions.
- Parameterize values and quote identifiers safely.

### Secrets and integrations
- No secrets in source, logs, fixtures, screenshots or docs.
- Use secret manager in deployed environments and ignored local env files.
- Explicit human approval before connecting accounts or enabling integrations.

### Privacy and retention
- Define retention and deletion before production.
- Minimize collected data and avoid raw values in logs/traces.
- Ensure exports, backups and derived artifacts follow deletion policy.
- Do not train models on customer uploads unless a separately approved, explicit opt-in design exists.

## Required security tests

- Tenant isolation matrix.
- IDOR tests.
- Malicious CSV/XLSX fixtures.
- Formula/macro non-execution tests.
- Prompt injection in cells/headers.
- SQL/tool allowlist bypass tests.
- Resource exhaustion and zip-bomb tests.
- Signed URL expiry and ownership tests.
- Secret scanning and dependency vulnerability scanning.
