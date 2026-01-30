# Pattern: Snapshot-Based Operational Analytics (LOAA)

## Use case
Operational data changes retroactively due to late documentation, corrections,
and re-exports. Leadership still needs metrics that are stable, explainable,
and comparable week over week.

This pattern supports decision-making without overwriting history or relying on
fragile spreadsheets.

---

## Core problem
When teams compute metrics directly from the “latest” version of operational
data, historical numbers drift. This creates confusion, mistrust, and endless
reconciliation conversations.

The core problem is **mutability of source data over time**.

---

## Approach

### 1. Ingest and archive raw inputs
- Accept multiple operational inputs per run (e.g., master lists, service logs, contextual notes)
- Archive raw files before transformation
- Treat each run as an auditable event

### 2. Normalize into canonical forms
- Standardize identifiers, dates, and categorical fields
- Resolve common data issues (Excel formatting, inconsistent IDs, missing values)
- Ensure all downstream logic operates on normalized data only

### 3. Snapshot by time period
- Write normalized records into snapshot tables keyed by time period (e.g., week_start)
- Preserve prior snapshots instead of overwriting data
- Treat snapshots as immutable once written

### 4. Compute rollups and signals from snapshots
- Aggregate metrics from snapshots, not raw files
- Generate leadership rollups, per-client views, and investigation signals
- Keep computation deterministic and repeatable

### 5. Persist outputs for traceability
- Store computed outputs alongside metadata (run date, inputs used)
- Support “what changed?” and week-over-week comparisons
- Enable downstream reporting without recomputation

---

## Why snapshotting matters
Snapshotting converts a moving target into a stable reference point.

It allows teams to:
- Compare metrics across time confidently
- Reproduce past decisions
- Audit how numbers were derived
- Separate data correction issues from performance issues

---

## Tradeoffs
- Requires more storage than overwriting data
- Adds upfront schema and lifecycle design
- Slightly more complex than spreadsheet-based workflows

These tradeoffs are intentional in exchange for **trust, explainability, and auditability**.

---

## What this pattern intentionally avoids
- Real-time mutation of historical metrics
- Black-box scoring or opaque ML models
- Tight coupling between ingestion, computation, and presentation
- Assumptions that source data is ever “final”

---

## Where this pattern is useful
- Operational analytics dashboards
- Weekly or monthly leadership reporting
- Compliance and audit workflows
- Programs with retroactive data correction
- Any environment where “why did this number change?” matters

---

## Summary
The LOAA pattern treats time as a first-class dimension of data.

By snapshotting normalized operational data and computing metrics from those
snapshots, teams gain stable insights without losing the ability to adapt as
source data evolves.
