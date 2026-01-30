# Pattern: Rule & Requirement Lifecycle Tracking

## Use case
Teams are expected to comply with changing rules, requirements, and deadlines,
often relying on memory, spreadsheets, or informal reminders.

Missed updates or expirations create compliance risk and operational disruption.

---

## Core problem
Compliance knowledge tends to live in tribal memory rather than structured systems.
When ownership changes or rules are updated, information becomes fragmented and
unreliable.

The core problem is **unstructured rule lifecycle management**.

---

## Approach

### 1. Treat rules as first-class records
- Store each rule or requirement as a structured entry
- Capture source, scope, and applicability
- Avoid embedding rules only in documents or emails

### 2. Track ownership and responsibility
- Assign a clear owner for each rule
- Make accountability explicit rather than implied
- Enable fast escalation when clarification is needed

### 3. Model time explicitly
- Record effective dates and expiration dates
- Generate alerts based on time, not memory
- Support upcoming, active, and expired states

### 4. Preserve change history
- Track when rules are updated
- Record what changed and why
- Maintain an audit-friendly trail of decisions

---

## Why lifecycle tracking matters
Rules are not static.

Tracking the lifecycle of requirements allows teams to:
- Respond to changes proactively
- Explain why a decision was compliant at the time
- Reduce dependency on individual memory

---

## Tradeoffs
- Requires discipline to keep records current
- Simpler than full policy engines
- Less flexible than ad-hoc notes

These tradeoffs favor reliability over convenience.

---

## What this pattern intentionally avoids
- Encoding business logic directly into prose documents
- Relying on reminders without source context
- Treating compliance as a one-time checklist
- Overengineering with complex rule engines

---

## Where this pattern is useful
- Compliance and regulatory tracking
- Policy and procedure management
- License, permit, or certification monitoring
- Any environment where rules change over time

---

## Summary
This pattern replaces tribal knowledge with structured ownership and time-based
tracking.

By modeling rules explicitly and preserving their history, teams can make
defensible, repeatable compliance decisions.

