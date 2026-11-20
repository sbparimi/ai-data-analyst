# Testing and Evaluation Strategy

## Test layers

1. Unit: pure domain logic, parsing, metrics and validation.
2. Property-based: aggregation invariants, transformations and edge cases.
3. Integration: database, object storage, queue and worker.
4. API: contracts, auth, tenant isolation and error semantics.
5. E2E: upload to insight to dashboard/report.
6. Security: malicious files, prompt injection, SQL/tool bypass, IDOR and resource exhaustion.
7. AI evaluation: groundedness, tool selection, abstention and explanation quality.
8. Performance: realistic dataset sizes and concurrent jobs.

## Golden datasets

Create synthetic, versioned fixtures for:
- Retail sales
- E-commerce orders
- Financial statements
- Marketing campaigns
- Customer churn
- Inventory
- SaaS subscriptions
- Operations
- Manufacturing
- Synthetic healthcare operations (no real patient data)

Each fixture must include source file, schema, deterministic expected values, known quality issues, known anomalies, expected findings, unsupported conclusions and evaluation questions.

## Numerical testing rules

- Expected values must be computed independently from the implementation under test.
- Use explicit decimal/currency handling where required.
- Define tolerances per metric.
- Test nulls, duplicates, zero denominators, negative values, timezone boundaries, mixed types, empty data, huge values and rounding.
- Test that results remain reproducible for the same dataset version and operation spec.

## AI evaluation rules

- Keep model/provider/version and prompt version with evaluation results.
- Evaluate against fixed fixtures and adversarial cases.
- Separate tool-selection accuracy from numerical correctness.
- Verify every claim maps to evidence.
- Penalize unsupported specificity and failure to abstain.
- Do not use LLM-as-judge as the sole correctness oracle.
- Use deterministic assertions for numerical claims.

## Definition of test completion

Record exact command, environment, commit SHA, exit code, summary, skipped tests and known failures in `harness/`.
