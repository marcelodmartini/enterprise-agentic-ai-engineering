# Week 16 — Event-Driven AI & Streaming Decisioning

**Focus:** Turn fintech events into timely signals, governed decisions and auditable actions

**Expected deliverable:** Event-Driven AI v1 with validated contracts, event-time windows, signal detection and safe policies.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **Kafka / API / CDC event** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Contract + dedupe** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Event-time window** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Signal engine** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Context graph + policy** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **HITL or safe action** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **Audit event** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### Event architecture

- An event records what happened; a command asks to act.
- Use versioned event contracts and schema compatibility.
- At-least-once delivery requires consumer idempotency.
- Ordering is scoped to a partition or chosen key.
- Exactly-once claims do not remove all external side effects.
- Keep event ID, correlation ID, source and timestamp.

### Time and stream semantics

- Event time is when the business fact occurred.
- Processing time is when the system receives it.
- Watermarks estimate progress amid late arrivals.
- Windows aggregate activity by count and time.
- Stateful processing keeps bounded per-key history.
- Choose lateness handling and retention explicitly.

### Source and ingestion

- Connect approved Kafka/MSK, CDC and webhook feeds.
- Validate schema and reject malformed event payloads.
- Use inbox/deduplication keyed by event identity.
- Enrich only with authorized business context.
- Route failed or poison messages to a DLQ.
- Monitor lag, throughput and schema failures.

### AI signal engine

- Detect unusual amount or transaction velocity.
- Combine deterministic rules with bounded model analysis.
- Compare current window with valid baseline.
- Record signal type, severity and evidence IDs.
- Query GraphRAG when connected context is useful.
- Do not treat model score as a confirmed fraud finding.

### Policy and decisioning

- Policy distinguishes alert from irreversible action.
- Auto-create informational case drafts when permitted.
- Require human review for blocking or financial changes.
- Use idempotency key on every external side effect.
- Deny action when critical context or policy is missing.
- Publish the decision, rationale and audit record.

### Fintech example

- Receive payment.authorized for an active merchant.
- Aggregate recent merchant risk signals by event time.
- Compare deviations against approved thresholds.
- Retrieve linked transaction, rule and deploy context.
- Generate an evidence-based analyst alert.
- Leave blocking / dispute decision to authorized process.

### Metrics and reliability

- Event lag and window completeness.
- Schema validity, duplicate event and DLQ rates.
- Signal precision, recall and analyst override.
- Decision latency end to end and by stage.
- Sensitive-action approval coverage and audit completeness.
- Cost per 1,000 processed events and alert usefulness.

### Build and exercise

- Implement schema validator and idempotency store.
- Add event-time window and watermark manager.
- Create rule/AI signal detector with typed outputs.
- Build deterministic decision policy and audit.
- Simulate late, duplicated and conflicting events.
- Demonstrate one end-to-end real-time chargeback signal.

### Exit checklist

- Explain event vs command and time semantics.
- Show valid schema evolution and event dedupe.
- Handle late events, replay and poison messages.
- Separate signals from authoritative decisions.
- Enforce HITL for sensitive outcomes.
- Deliver streaming demo, metrics and trace.

## Hands-on training schedule

- **Monday:** Review **Event architecture** and **Time and stream semantics**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Source and ingestion** and **AI signal engine**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **AI signal engine** and **Policy and decisioning**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Policy and decisioning** and **Fintech example**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Metrics and reliability** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- Policy distinguishes alert from irreversible action.
- Auto-create informational case drafts when permitted.
- Require human review for blocking or financial changes.
- Use idempotency key on every external side effect.
- Deny action when critical context or policy is missing.
- Publish the decision, rationale and audit record.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
