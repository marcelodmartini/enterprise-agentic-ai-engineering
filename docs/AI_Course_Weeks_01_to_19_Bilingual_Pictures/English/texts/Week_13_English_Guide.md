# Week 13 — AI Platform Engineering, Gateway & Control Plane

**Focus:** Standardize the reusable platform shared across enterprise fintech AI products

**Expected deliverable:** Enterprise AI Control Plane v1 with governed registries, routing and gateway policies.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **AI product / tenant** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Gateway and identity** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Model / prompt / tool registries** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Policy + router** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Runtime data plane** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **Telemetry and release gates** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### Platform versus application

- An AI application solves one user-facing use case.
- An AI platform supplies shared infrastructure and governance.
- Control plane configures policy, registries and versions.
- Data plane executes actual requests and tool calls.
- A gateway enforces common controls at the boundary.
- Do not duplicate security decisions across every team.

### Governed registries

- Model registry records versions, providers and access.
- Prompt registry stores templates and approvals.
- Tool registry catalogs schemas, scopes and owners.
- Tenant registry isolates budgets, policies and domains.
- Release registry links changes to tests and approvals.
- All registry entries need stable IDs and lifecycle.

### Gateway request path

- Authenticate user and resolve tenant and purpose.
- Validate allowed model, prompt and tool capabilities.
- Check quotas, data classifications and policy rules.
- Route to provider through a normalized interface.
- Validate output and manage provider faults.
- Emit consistent traces, metering and audit records.

### Model selection

- Compare capability, region, latency, cost and risk.
- Limit providers and model families by tenant policy.
- Resolve model alias to a pinned concrete revision.
- Use fallback only when approved semantics remain safe.
- Record chosen version and routing rationale.
- Prevent unsupported data residency or egress.

### Fintech example

- A chargeback agent requests a model and payment tool.
- Gateway resolves team, environment and risk tier.
- Registries find approved tool and prompt versions.
- Policy permits read-only evidence retrieval.
- Model response includes sources and task outcome.
- Metrics and approval status attach to request ID.

### Policy as code

- Express allow/deny rules outside model prompts.
- Use RBAC/ABAC and least-privilege tool scopes.
- Enforce token, cost and call-count limits.
- Require human approval for high-impact operations.
- Deny unknown models and unreviewed prompt changes.
- Produce an auditable decision for each gate.

### Operational metrics

- Gateway request success, p95 and provider latency.
- Model usage by team, tenant and use case.
- Tool policy denies and sensitive-action attempts.
- Prompt/model version adoption and regressions.
- Tokens, unit cost and budget consumption.
- Availability and release gate compliance.

### Build and exercise

- Implement model, prompt, tool and tenant registries.
- Create provider-neutral AI gateway and policy engine.
- Add cost-aware router, fake provider and telemetry.
- Implement release checks for eval and security.
- Test cross-tenant access and unknown model requests.
- Document an integrated product-to-platform demo.

### Exit checklist

- Explain control plane versus data plane.
- Show one enforcement point for shared policy.
- Pin versions, scopes and tenant boundaries.
- Route models with logged rationale.
- Demonstrate release gate and rollback plan.
- Deliver enterprise gateway with reproducible tests.

## Hands-on training schedule

- **Monday:** Review **Platform versus application** and **Governed registries**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Gateway request path** and **Model selection**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Model selection** and **Fintech example**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Fintech example** and **Policy as code**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Operational metrics** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- A chargeback agent requests a model and payment tool.
- Gateway resolves team, environment and risk tier.
- Registries find approved tool and prompt versions.
- Policy permits read-only evidence retrieval.
- Model response includes sources and task outcome.
- Metrics and approval status attach to request ID.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
