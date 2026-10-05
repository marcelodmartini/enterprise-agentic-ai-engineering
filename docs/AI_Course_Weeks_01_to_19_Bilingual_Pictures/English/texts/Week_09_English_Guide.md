# Week 09 — AI Observability, Tracing, Latency & Cost

**Focus:** Explain what an agent did, why it did it and how much each stage cost

**Expected deliverable:** An instrumented fintech AI runtime with request traces, useful dashboards and actionable alerts.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **Incoming request** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Trace root** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Retrieval spans** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Tool spans** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Model spans** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **Validation** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **Metrics, logs and dashboard** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### Observability versus monitoring

- Monitoring checks expected signals and alarms.
- Observability helps diagnose unknown failure modes.
- A trace links one request across several components.
- A span describes a timed operation inside the trace.
- Metrics aggregate rates, durations, quality and costs.
- Logs add event detail without leaking private content.

### Trace design

- Propagate requestId, traceId, workflowId and tenant scope.
- Create spans for auth, retrieval, tool, model and policy.
- Record outcome, duration, version and error category.
- Preserve source IDs and data freshness metadata.
- Link retries and human approvals to the parent case.
- Avoid storing raw card data, secrets or full sensitive prompts.

### Latency breakdown

- Separate queue wait, retrieval, tool and model time.
- Measure p50, p95 and p99 rather than mean only.
- Observe first-token and full-response latency when useful.
- Attribute timeouts to the responsible dependency.
- Track retries and fallback-related delays.
- Use stage budgets to identify critical paths.

### Cost and quality signals

- Record input, cached-input and output usage.
- Attribute model and tool costs by use case.
- Track evidence availability and answer groundedness.
- Record JSON validity and tool-call correctness.
- Connect offline evaluation version to runtime traces.
- Compare successful-case cost, not just total tokens.

### Fintech debugging

- A dispute answer lacks a current policy citation.
- Use trace to locate retrieval and reranker stages.
- Check which document version was returned.
- Inspect tool authorization and model context IDs.
- Correlate with indexer deploy and dataset freshness.
- Fix responsible stage rather than changing prompt blindly.

### Dashboards and alerts

- Display traffic, errors and saturation by domain.
- Show p95 end-to-end and by-stage latency.
- Trend token spend and cost per resolved case.
- Alert on groundedness and unsafe action failures.
- Monitor tool timeouts, empty retrieval and schema failures.
- Every alert links to a clear owner and runbook.

### Privacy and governance

- Use bounded retention and restricted trace access.
- Hash or redact user and transaction identifiers.
- Separate diagnostic metadata from raw business data.
- Audit access to sensitive telemetry.
- Version prompts, policies, retrievers and model IDs.
- Treat observability data as potentially confidential.

### Build and exercise

- Instrument fake retriever, tools and model with spans.
- Build metrics collector and structured event logger.
- Create a minimal dashboard of quality, latency and cost.
- Inject a slow tool and a missing-evidence failure.
- Use trace to isolate each failing stage.
- Deliver sample trace, dashboard and runbook.

### Exit checklist

- Explain trace, span, metric and structured log.
- Correlate one case from input through output.
- Find expensive or slow pipeline stages.
- Track evidence and validation failures.
- Protect telemetry from excessive sensitive content.
- Deliver instrumented AI runtime and diagnostic guide.

## Hands-on training schedule

- **Monday:** Review **Observability versus monitoring** and **Trace design**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Latency breakdown** and **Cost and quality signals**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Cost and quality signals** and **Fintech debugging**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Fintech debugging** and **Dashboards and alerts**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Privacy and governance** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- A dispute answer lacks a current policy citation.
- Use trace to locate retrieval and reranker stages.
- Check which document version was returned.
- Inspect tool authorization and model context IDs.
- Correlate with indexer deploy and dataset freshness.
- Fix responsible stage rather than changing prompt blindly.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
