# Week 19 — AI FinOps, Cost Governance & Model Routing

**Focus:** Keep enterprise fintech AI financially accountable while preserving quality and safety

**Expected deliverable:** AI FinOps control plane with usage metering, budgets, routing, capacity planning and value reporting.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **AI request** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Meter tokens / tools** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Evaluate budget + quota** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Select model / cache / batch** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Run safely** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **Allocate cost** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **Measure outcome and optimize** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### Measure total AI cost

- Attribute usage to request, workflow, user and domain.
- Track input, cached-input, output and reasoning tokens.
- Add retrieval, tool, storage, retries and review costs.
- Use configurable pricing by provider, model and date.
- Report cost per successful business resolution.
- Distinguish cost avoidance from realized financial savings.

### Unit economics and value

- Cost per workflow includes all activities and tools.
- Compare outcome against a documented manual baseline.
- Estimate analyst time saved and actual quality impact.
- Include risk reduction and fewer repeat operations.
- Showback displays consumption by team or domain.
- Internal chargeback assigns costs only by agreed policy.

### Budgets, quotas and limits

- Budget caps permitted spend over a defined interval.
- Quota limits requests, tokens or premium-model use.
- Rate limit caps request velocity and provider saturation.
- Use warning, degrade and noncritical block thresholds.
- Reserve capacity for higher-criticality business flows.
- Do not weaken safety controls merely to lower cost.

### Cost-aware model router

- Route by risk, complexity, evidence and latency need.
- Use efficient models for simple approved tasks.
- Choose deeper reasoning where validated need exists.
- Prefer batch for offline tasks without a waiting user.
- Log chosen model and budget-aware routing rationale.
- Human approval still governs all sensitive actions.

### Context and cache optimization

- Reuse stable prompt prefixes when provider supports caching.
- Measure actual cached-token usage and hit rate.
- Deduplicate RAG chunks; reduce top-k only after eval.
- Load only relevant tool descriptors and schemas.
- Trim conversation history while preserving critical facts.
- Never sacrifice evidence or permissions for shorter prompts.

### Capacity and anomalies

- Forecast request and token demand by minute/day.
- Plan concurrency, queues, batch windows and p95 peaks.
- Reserve headroom for rate limits and priority workloads.
- Alert on cost spikes, retry storms and cache-hit collapse.
- Investigate shifts in model, prompt, tool and traffic.
- Track unit-cost SLOs next to quality and safety SLOs.

### Chargeback business case

- Meter each solve-chargebacks request end to end.
- Allocate model, graph, Snowflake and review costs.
- Compare resolved cases to a measured manual baseline.
- Choose model based on complexity and business risk.
- Use safe cost-degraded mode for optional capabilities.
- Report quality, resolution time, cost and ROI assumptions.

### Build and exercise

- Implement price catalog and usage events.
- Calculate total request/workflow costs and budgets.
- Build quota, router, cache and batch decisions.
- Create capacity plan and cost anomaly alerts.
- Produce showback by domain and use case.
- Test budget breach without bypassing security policy.

### Exit checklist

- Calculate cost per request, workflow and resolution.
- Use configurable model rates and clear assumptions.
- Enforce budgets, quotas and routing transparently.
- Demonstrate safe caching, batching and degradation.
- Show cost anomalies alongside quality outcomes.
- Deliver FinOps report and optimization backlog.

## Hands-on training schedule

- **Monday:** Review **Measure total AI cost** and **Unit economics and value**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Budgets, quotas and limits** and **Cost-aware model router**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Cost-aware model router** and **Context and cache optimization**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Context and cache optimization** and **Capacity and anomalies**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Chargeback business case** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- Reuse stable prompt prefixes when provider supports caching.
- Measure actual cached-token usage and hit rate.
- Deduplicate RAG chunks; reduce top-k only after eval.
- Load only relevant tool descriptors and schemas.
- Trim conversation history while preserving critical facts.
- Never sacrifice evidence or permissions for shorter prompts.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
