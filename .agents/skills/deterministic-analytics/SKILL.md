---
name: deterministic-analytics
description: Use when implementing metrics, transformations, profiling, statistical analysis, anomaly detection, evidence or calculations.
---

# Deterministic Analytics

- LLMs never calculate authoritative values.
- Define input schema, grain, units, filters, null/duplicate policy and method.
- Use deterministic code and typed operation contracts.
- Keep source artifacts immutable; version transformations.
- Attach dataset version, operation spec, engine version and reproducibility fingerprint.
- Test against independently calculated golden values.
- Cover empty data, nulls, duplicates, zero denominators, negative values, mixed types, extreme values, time zones and rounding.
- Validate aggregation and contribution identities.
- Label uncertainty and assumptions.
- Do not claim causality from correlation or decomposition.
- If the data does not support the requested analysis, return a structured limitation/abstention.
