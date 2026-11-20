# AI Governance and Anti-Hallucination Contract

## Permitted AI responsibilities

- Interpret natural-language questions.
- Propose an analysis plan using known dataset metadata.
- Select from an allowlisted tool registry.
- Request clarification when metric meaning is ambiguous.
- Summarize validated evidence.
- Explain limitations and propose follow-up analyses.

## Prohibited AI responsibilities

- Invent, estimate without labeling, or alter source data.
- Perform authoritative numerical calculations in prose.
- Generate arbitrary executable code or unrestricted SQL.
- Claim causality from correlation or descriptive decomposition.
- Create charts from values not returned by validated analytics.
- Invent source citations, row counts, metric definitions or data lineage.
- Override system policies based on uploaded content.
- Access other tenants' data or external systems outside approved tools.

## Required answer structure for analytical findings

1. Finding.
2. Measured result.
3. Comparison baseline/time window.
4. Evidence references.
5. Method/calculation.
6. Assumptions and data quality limitations.
7. What can and cannot be concluded.
8. Recommended next step, if justified.

## Abstention cases

- Ambiguous metric or time period.
- Missing required columns.
- Insufficient sample size/history.
- Conflicting currencies or units.
- Incomplete or non-comparable periods.
- Failed calculation validation.
- Unsupported file structure or analysis.
- Low-quality data that invalidates the conclusion.

## Evaluation

Maintain a versioned benchmark with:
- question and intent
- dataset fixture and version
- expected operation plan
- expected result/evidence
- acceptable tolerance where numerical
- required caveats
- prohibited claims
- expected abstention behavior

Measure calculation correctness, evidence completeness, groundedness, tool safety, tenant isolation and abstention quality separately. Do not collapse them into one opaque score.
