# Pattern: Snapshot-Based Operational Analytics

## Use case
Weekly operational data often changes retroactively. Metrics must remain stable,
explainable, and comparable over time despite late corrections or re-exports.

## Approach
- Normalize incoming data into canonical forms
- Write snapshots keyed by time period (e.g., week_start)
- Compute rollups from snapshots rather than raw files
- Preserve all historical states for traceability

## Tradeoffs
- Uses more storage than overwriting data
- Requires slightly more upfront structure
- Results in significantly higher trust and auditability

## Why this works
This pattern replaces fragile spreadsheet logic with deterministic,
repeatable computation that supports historical comparisons and audits.
