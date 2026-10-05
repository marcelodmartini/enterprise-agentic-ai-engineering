# Week 17 — Durable AI Workflows, HITL & Sagas

**Focus:** Run long-lived fintech processes that pause, recover, compensate and remain auditable

**Expected deliverable:** A chargeback investigation workflow with durable state, human approval, saga compensation and outbox.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **Event / request** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Persist workflow state** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Activities + bounded AI** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Policy gate** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Human pause / resume** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **Safe action + saga** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **Outbox and audit** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### Durability and state

- Workflows survive restart, deploy, timeout and long waits.
- Persist workflow ID, status, step, attempts and history.
- Activities perform I/O and other nondeterministic work.
- Deterministic workflow code replays recorded results.
- Checkpoint before and after meaningful transitions.
- Pin workflow, prompt, tool, policy and graph versions.

### Agent and activity roles

- Workflow defines the controlled business process.
- An agent analyzes evidence inside a bounded step.
- Activities call payments, merchant, fraud and model APIs.
- Return typed success, retryable or terminal failure.
- Bound retries, deadlines and tool budgets.
- Never run real side effects while replaying history.

### Formal human review

- Create durable approval request with reviewer scope.
- Persist WAITING_HUMAN_APPROVAL rather than polling RAM.
- Allow approve, reject and request-more-info decisions.
- Validate actor, intent, version and expiry on callback.
- Resume only the matching workflow and case.
- Timeout, escalate or expire without automatic risky action.

### Saga and compensation

- Saga coordinates multi-step distributed operations.
- A compensation neutralizes an already completed step.
- Cancel a draft case if a later required step fails.
- Release a reserved review slot after cancellation.
- Compensation may not fully reverse external effects.
- Record failed compensation and escalate for repair.

### Inbox, outbox and signals

- Inbox prevents duplicate processing of incoming events.
- Outbox stores pending publication with business state.
- A separate publisher retries until acknowledged.
- Signals resume workflow on approval or client action.
- Timers implement bounded review and timeout policy.
- Carry correlation IDs across services and Kafka topics.

### Chargeback example

- chargeback.created starts a durable investigation.
- Load payment, merchant and fraud evidence.
- Generate summary, classify risk and evaluate policy.
- Pause high-risk case for authorized analyst.
- On approval create idempotent case draft and outbox event.
- On rejection/timeout close safely and audit.

### Operational controls

- Measure waiting, completed, failed and stuck workflows.
- Track approval latency, activity retries and sagas.
- Record side effect IDs and duplicate prevention.
- Use separate queues for time-sensitive workloads.
- Alert on timeout, compensation and publish failures.
- Protect private case data in state, history and logs.

### Build and exercise

- Implement state store, history and typed transitions.
- Create activity runner and retry classes.
- Build approval queue with callback, expiry and escalation.
- Add saga compensation and inbox/outbox simulation.
- Test replay after restart without duplicate action.
- Emit auditable final state and trace.

### Exit checklist

- Explain durable execution and deterministic replay.
- Demonstrate pause, approval and safe resumption.
- Keep side effects idempotent with compensation.
- Show inbox/outbox consistency approach.
- Test timeouts, failures and version compatibility.
- Deliver chargeback workflow, tests and audit record.

## Hands-on training schedule

- **Monday:** Review **Durability and state** and **Agent and activity roles**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Formal human review** and **Saga and compensation**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Saga and compensation** and **Inbox, outbox and signals**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Inbox, outbox and signals** and **Chargeback example**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Operational controls** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- Inbox prevents duplicate processing of incoming events.
- Outbox stores pending publication with business state.
- A separate publisher retries until acknowledged.
- Signals resume workflow on approval or client action.
- Timers implement bounded review and timeout policy.
- Carry correlation IDs across services and Kafka topics.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
