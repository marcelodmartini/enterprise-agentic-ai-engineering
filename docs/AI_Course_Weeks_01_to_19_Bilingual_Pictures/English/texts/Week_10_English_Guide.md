# Week 10 — AI Security, Prompt Injection & Scoped Tools

**Focus:** Build a threat-aware fintech agent where instructions, data and actions have distinct trust levels

**Expected deliverable:** Secure AI Runtime v1 with prompt-injection defenses, least privilege and approval-gated actions.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **Request + retrieved content** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Threat and scope checks** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Bounded model reasoning** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Tool policy gate** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Authorized execution** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **Output guardrails** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **Audit** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### Threat model

- Direct injection comes from a malicious user instruction.
- Indirect injection hides in a document, tool result or page.
- Tool abuse tries to trigger an unauthorized operation.
- Data leakage reveals confidential information or secrets.
- Model output can suggest harmful actions while sounding valid.
- The model cannot be the sole security enforcement point.

### Trust boundaries

- System and developer policy outrank untrusted content.
- Mark retrieved text, emails and logs as data only.
- Never execute instructions embedded in evidence.
- Keep tool authorization in deterministic application code.
- Protect service credentials from the model context.
- Validate both user intent and downstream action arguments.

### Least-privilege tools

- Give each tool explicit read/write capability and scope.
- Authorize resource, tenant, role and business purpose.
- Reject dynamic tool names not on the allowlist.
- Separate read-only exploration from side effects.
- Require a distinct approval gate for sensitive actions.
- Use idempotency keys and audit for permitted writes.

### Input and output guards

- Detect obvious secret and PII disclosure attempts.
- Validate JSON, citations and allowed field values.
- Avoid unsupervised model statements of confirmed fraud.
- Prevent policy leakage in customer-facing responses.
- Treat missing evidence as insufficient, not permissive.
- Record guard decisions with minimal retained payload.

### Fintech scenario

- A retrieved dispute note says to ignore system rules.
- The boundary labels the note as untrusted evidence.
- The model may summarize facts but cannot run hidden commands.
- A request to change a credit limit is policy-denied.
- Reviewer sees safe draft only when conditions are met.
- Audit records rejection and reason without copying PII.

### Approval and policy

- Policy engine evaluates action type and risk level.
- Use purpose limitation and environment-based scopes.
- Human approves final intent and authorized target.
- Expire approvals and prevent token replay.
- Fail closed on unavailable policy or unknown identity.
- Never allow a response format to imply permission.

### Security tests

- Direct and indirect injection suites.
- Cross-tenant data access attempts.
- Unauthorized tool and parameter fuzzing.
- Sensitive-output and secret-exposure checks.
- Replay, duplicate and excessive tool-call tests.
- Verify safe refusals are clear and actionable.

### Build and exercise

- Create tool registry with scopes and sensitivity.
- Implement untrusted-context delimiters.
- Add input, tool and output validation layers.
- Create policy evaluator and approval mock.
- Run malicious-document and denied-tool test cases.
- Ship secure runtime with auditable outcomes.

### Exit checklist

- Explain why prompt alone cannot enforce security.
- Identify user, tool and retrieval trust boundaries.
- Show fail-closed authorization for sensitive actions.
- Test indirect injection and PII leakage.
- Prove action approval and idempotency.
- Deliver threat model, test report and guardrails.

## Hands-on training schedule

- **Monday:** Review **Threat model** and **Trust boundaries**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Least-privilege tools** and **Input and output guards**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Input and output guards** and **Fintech scenario**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Fintech scenario** and **Approval and policy**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Security tests** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- A retrieved dispute note says to ignore system rules.
- The boundary labels the note as untrusted evidence.
- The model may summarize facts but cannot run hidden commands.
- A request to change a credit limit is policy-denied.
- Reviewer sees safe draft only when conditions are met.
- Audit records rejection and reason without copying PII.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
