---
name: tenant-isolation
description: Use when implementing or changing authentication, workspace/project resources, queries, storage, jobs, caches, exports or authorization.
---

# Tenant Isolation

- Tenant scope comes from authenticated membership, never client-supplied tenant identifiers.
- Authorize every resource read, write, list, export and background job.
- Propagate tenant context explicitly to workers.
- Include tenant in storage object ownership and cache keys.
- Enforce scope in database queries and consider row-level security.
- Test cross-tenant IDOR for every resource and nested relationship.
- Test exports, signed URLs, async jobs, logs and notifications.
- Default deny. Missing membership means no access.
