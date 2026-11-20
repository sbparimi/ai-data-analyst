---
name: secure-file-ingestion
description: Use when handling uploaded CSV/XLSX files, parsers, object storage or data previews.
---

# Secure File Ingestion

- Treat all files and metadata as malicious/untrusted.
- Validate content signatures and parser behavior, not only extension.
- Enforce file, decompression, sheet, row, column, cell, memory and runtime limits.
- Parse in isolated workers with least privilege and no unnecessary network.
- Never execute formulas, macros, scripts, external links or embedded objects.
- Preserve immutable original artifact and create versioned derived artifacts.
- Avoid logging raw values.
- Test malformed files, zip bombs, oversized dimensions, encoding issues, formula cells and prompt injection payloads.
- Ensure tenant ownership checks for upload, processing, preview, download and deletion.
