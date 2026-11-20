# Analytics and Evidence Specification

## 1. Metric contract

Every metric definition must specify:
- Stable metric ID and version.
- Human-readable name and description.
- Numerator/denominator or aggregation expression.
- Grain and grouping dimensions.
- Unit/currency.
- Time field and timezone assumptions.
- Filters and exclusions.
- Null and duplicate handling.
- Minimum data requirements.
- Known limitations.

## 2. Supported initial analytical operations

Start with a small allowlist:
- row/column counts
- null/unique/duplicate profiling
- min/max/mean/median/quantiles/stddev
- frequency and distribution summaries
- group-by aggregations
- time-bucket aggregation
- period-over-period comparison
- contribution/decomposition by dimension
- correlation with sample-size and caveat checks
- bounded outlier/anomaly methods with explicit parameters

Do not imply that correlation proves causation. Do not apply time-series methods when the data is not a valid time series.

## 3. Evidence record

An evidence record should include:
- evidence_id
- dataset_version_id
- analysis_run_id
- operation_id
- metric_definition_id/version where relevant
- input filters and dimensions
- calculation method and parameters
- result schema and values
- units and time window
- source row/partition references where feasible
- execution timestamp and engine version
- warnings, assumptions and limitations
- reproducibility fingerprint

Avoid exposing sensitive raw row values by default.

## 4. Insight contract

Each insight must include:
- insight_id and type
- concise title and explanation
- priority rationale
- evidence IDs
- calculation and comparison window
- uncertainty/confidence basis, not an arbitrary model score
- assumptions and limitations
- suggested next analysis/action
- validation status

## 5. Validation

- Recompute critical totals independently in tests.
- Validate aggregation identities and contribution sums.
- Check denominator zero/near-zero.
- Check missing periods and inconsistent granularity.
- Check currency/unit consistency.
- Check sample sizes and statistical assumptions.
- Detect leakage between training and evaluation periods for forecasts.
- Ensure chart data exactly matches evidence result.
- Reject or qualify findings that fail validation.

## 6. Forecasting

Forecasting is not MVP-critical. Before release:
- Define supported time series and minimum history.
- Compare against naive/seasonal-naive baselines.
- Use rolling-origin backtesting.
- Report prediction intervals and evaluation window.
- Detect structural breaks and missing periods.
- Abstain when data is insufficient.
- Never present forecast as certainty.

## 7. Recommendation impact

Impact estimates must be calculated from explicit assumptions and source metrics. Label scenario estimates as scenarios, not observed facts. Do not assert causal impact without a suitable causal design.
