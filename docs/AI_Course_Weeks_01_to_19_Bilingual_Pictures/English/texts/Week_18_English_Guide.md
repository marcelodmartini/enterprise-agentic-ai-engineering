# Week 18 — AI Reliability, SLOs, Incidents & Chaos

**Focus:** Operate RAG, agents and durable workflows safely when production dependencies fail

**Expected deliverable:** An AI reliability control plane with SLO tracking, runbooks, controlled degradation and chaos scenarios.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **Product traffic** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Collect SLIs** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Evaluate SLO and budget** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Burn-rate alert** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Incident / runbook** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **Safe degradation or rollback** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **Postmortem** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### Reliability foundations

- Observability says what happened; reliability governs response.
- An SLI measures a user-relevant service outcome.
- An SLO defines a target over a documented time window.
- An SLA is a contractual commitment, if applicable.
- Error budget is tolerated bad-event or downtime allowance.
- Burn rate measures how quickly that budget is consumed.

### Failure categories

- Technical: provider timeout, rate limit, Kafka lag.
- Context: stale policy, missing evidence or graph path.
- AI quality: unsupported answer or malformed JSON.
- Policy: unauthorized tool or unapproved action.
- Operational: stuck workflow, duplicate case or DLQ growth.
- Economic: excessive retries, tokens and case cost.

### AI-specific SLOs

- Availability and p95 end-to-end latency.
- Grounded answer and valid structured-output rate.
- Tool correctness, retrieval evidence and source freshness.
- Sensitive-action approval and policy violation rate.
- Workflow completion and human review latency.
- Cost per resolved case and audit completeness.

### Controlled degradation

- Graph unavailable: use certified documentary evidence.
- Model unavailable: return safe template or human handoff.
- Policy unavailable: fail closed for sensitive actions.
- Outbox unavailable: avoid unrecorded side effects.
- Circuit breaker isolates repeatedly failing tools.
- Bulkhead, retry budget and timeouts contain blast radius.

### Incident handling

- Detect, triage and assign severity using impact.
- Contain unsafe capabilities with feature flags / kill switch.
- Use documented runbook for safe mitigation.
- Record incident timeline, owner and communication.
- Rollback or reduce model/graph functionality when needed.
- Write postmortem and tracked reliability actions.

### Chaos and release

- Inject controlled model, graph and tool failures.
- Simulate bad JSON, stale data and approval backlog.
- Verify safe degraded mode and audit completion.
- Test shadow, canary and rollback procedures.
- Gate release on eval, policy and critical chaos tests.
- Start in test/staging before controlled production trials.

### Fintech example

- Graph DB fails during a chargeback investigation.
- Trace shows missing graph evidence and SLO burn.
- Switch to authorized document-only response.
- Block sensitive actions and queue analyst review.
- Recover graph, rerun validations and lift restriction.
- Document incident and prevent recurrence.

### Build and exercise

- Implement SLI collector, SLO evaluator and burn alert.
- Add feature flags, breaker and degradation rules.
- Build runbook lookup and incident state machine.
- Execute graph-down, model-down and policy-down chaos tests.
- Create postmortem and owner-specific reliability backlog.
- Report before/after service outcomes.

### Exit checklist

- Define windows, owners and calculation of SLOs.
- Show safe fail-closed mode for sensitive actions.
- Trace alert to runbook, containment and recovery.
- Prove recovery under injected critical faults.
- Validate feature flag, canary and rollback.
- Deliver reliability demo and incident documentation.

## Hands-on training schedule

- **Monday:** Review **Reliability foundations** and **Failure categories**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **AI-specific SLOs** and **Controlled degradation**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Controlled degradation** and **Incident handling**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Incident handling** and **Chaos and release**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Fintech example** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- Detect, triage and assign severity using impact.
- Contain unsafe capabilities with feature flags / kill switch.
- Use documented runbook for safe mitigation.
- Record incident timeline, owner and communication.
- Rollback or reduce model/graph functionality when needed.
- Write postmortem and tracked reliability actions.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
