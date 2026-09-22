# Week 11 — AI Production Readiness & Resilience

**Focus:** Make fintech AI services dependable under load, provider faults and distributed retries

**Expected deliverable:** A production-ready runtime design with resilience patterns, budgets, queues and deployment gates.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **Client** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **API gateway + limits** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Runtime + policy** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Resilient provider / tools** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Async queue when needed** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **Verified response** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **SLO and audit** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### Service objectives

- Define functional and nonfunctional requirements.
- Measure availability, reliability and recoverability.
- Choose service-level indicators and objectives.
- Use p95/p99 latency for user-perceived performance.
- Set error budgets for controlled delivery decisions.
- Design separate readiness and liveness checks.

### Resilience toolkit

- Set a deadline before calling remote dependencies.
- Retry transient errors with exponential backoff and jitter.
- Circuit breaker prevents cascading failures.
- Bulkheads isolate domains and expensive workloads.
- Concurrency and token-bucket limits bound load.
- Avoid retry storms and unintended duplicate actions.

### Consistency and queues

- Use idempotency keys for requests with side effects.
- At-least-once delivery requires deduplication.
- Queue long tasks to decouple request and execution.
- Dead-letter failed items for supervised reprocessing.
- Preserve correlation and retry-attempt metadata.
- Handle outbox/inbox where state and events must agree.

### Caching and routing

- Cache safe responses, documents and provider metadata.
- Define TTL, invalidation, tenant-aware keys.
- Use single-flight to mitigate cache stampedes.
- Route models by task, risk, cost and latency.
- Fallback must not silently weaken semantics or security.
- Measure cache hit and model-specific failure rate.

### Fintech example

- Chargeback analyst invokes internal solve endpoint.
- Gateway authenticates and rate-limits the request.
- RAG and tools run under a common deadline.
- Unresponsive graph service triggers evidence-only mode.
- Any high-risk write waits for authorized review.
- Response identifies partial data and logs its trace.

### Multi-tenancy and safety

- Separate data, budgets and credentials by tenant.
- Apply least privilege to every provider and tool.
- Encrypt sensitive persistence and minimize prompt data.
- Guard automated writes with policy and human approval.
- Keep an immutable or tamper-evident audit path.
- Fail safely when required controls are unavailable.

### Release and operations

- Use unit, integration, contract and evaluation tests.
- Deploy by rolling, blue-green, canary or shadow.
- Monitor new model / prompt versions against baseline.
- Define rollback, feature flag and incident runbooks.
- Observe tokens, dollars, throughput and concurrency.
- Protect SLOs while performing controlled rollout.

### Build and exercise

- Implement timeouts, retry, breaker and token bucket.
- Create idempotency store and TTL cache.
- Add queue / DLQ simulation and provider fallback.
- Define request budgets and per-tenant limits.
- Inject dependency failures and measure degradation.
- Document production-readiness acceptance criteria.

### Exit checklist

- Demonstrate latency and availability objectives.
- Prevent duplicates after retry or replay.
- Bound queues, concurrency, tokens and cost.
- Provide safe failure and degraded modes.
- Show canary/rollback and release gate.
- Deliver architecture, tests and operational runbooks.

## Hands-on training schedule

- **Monday:** Review **Service objectives** and **Resilience toolkit**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Consistency and queues** and **Caching and routing**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Caching and routing** and **Fintech example**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Fintech example** and **Multi-tenancy and safety**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Release and operations** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- Chargeback analyst invokes internal solve endpoint.
- Gateway authenticates and rate-limits the request.
- RAG and tools run under a common deadline.
- Unresponsive graph service triggers evidence-only mode.
- Any high-risk write waits for authorized review.
- Response identifies partial data and logs its trace.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
