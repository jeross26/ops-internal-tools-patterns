# Pattern: Validation-First Reporting Pipeline

## Use case
Operational reports are often generated from CSV or Excel exports that contain
missing fields, inconsistent formats, or partial data.

Leadership still needs reports they can trust without hiding data quality issues
or producing misleading metrics.

---

## Core problem
Many reporting workflows silently drop bad rows or coerce invalid values.
This creates clean-looking reports that are directionally wrong and difficult
to defend when numbers are questioned.

The core problem is **implicit data loss during reporting**.

---

## Approach

### 1. Normalize inputs explicitly
- Load CSV/XLSX exports without assumptions
- Standardize column names, data types, and date formats
- Resolve common inconsistencies before analysis begins

### 2. Validate required fields
- Define required fields for each report
- Check for missing, invalid, or malformed values
- Treat validation as a first-class step, not an afterthought

### 3. Separate clean data from flagged data
- Retain all rows
- Route invalid or incomplete rows to a “needs review” dataset
- Ensure metrics are computed only from validated data

### 4. Compute metrics deterministically
- Calculate KPIs from validated data only
- Avoid implicit filtering or correction logic
- Keep calculations simple and explainable

### 5. Generate executive-ready outputs
- Produce consistent PDF reports for distribution
- Include charts, summaries, and watchlists
- Persist outputs so reports can be reproduced later

---

## Why validation-first matters
Surfacing data quality issues builds trust.

Instead of debating whether numbers are correct, teams can:
- See what data was excluded and why
- Address upstream process issues
- Improve data quality over time

---

## Tradeoffs
- Requires more upfront validation logic
- Slightly slower pipeline execution
- Produces more artifacts (clean vs flagged data)

These tradeoffs reduce downstream confusion and rework.

---

## What this pattern intentionally avoids
- Silent row drops or implicit coercion
- “Fixing” data without visibility
- Complex transformations that obscure logic
- Tight coupling to a specific UI or delivery mechanism

---

## Where this pattern is useful
- Weekly or monthly operational reporting
- Executive dashboards and board packets
- Compliance or audit-supporting reports
- Any workflow where data quality varies by source

---

## Summary
This pattern treats data quality as part of the reporting product.

By validating inputs explicitly and separating clean data from flagged data,
reports become more trustworthy, defensible, and actionable.

