# Week 02 — Structured Outputs, JSON Schema & Tool Calling

**Focus:** Move from free-form text to typed contracts and controlled external actions

**Expected deliverable:** A Tool Runtime v1: validated extraction, classification and read-only fintech tool dispatch.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **User request** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Classification / extraction** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **JSON Schema validation** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Tool selection** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Policy gate** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **Execute allowlisted tool** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **Validate and log result** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### Key distinctions

- Structured output is a format contract, not a truth guarantee.
- JSON Schema specifies types, required fields and constraints.
- Tool calling proposes an action; application code executes it.
- Extraction reads fields; classification assigns known categories.
- A tool response is untrusted until checked against contract.
- A valid JSON object can still contain a wrong fact.

### Schema essentials

- Use object and array types with required keys.
- Use enums for statuses, currency and reason codes.
- Use additionalProperties: false where appropriate.
- Separate nullable, optional and missing fields.
- Validate amounts, dates, lengths and nested objects.
- Version schemas when downstream consumers rely on them.

### Tool anatomy

- Give each tool one explicit business purpose.
- Publish name, description, input schema and output schema.
- Declare side effects and required permissions.
- Reject unknown arguments and unavailable tool names.
- Pass correlation IDs, deadlines and idempotency keys.
- Return typed errors rather than plausible invented data.

### Full execution path

- Interpret user intent under the system contract.
- Produce a structured tool-call proposal.
- Validate proposed arguments locally.
- Authorize identity, resource, domain and purpose.
- Invoke real handler; check and normalize tool output.
- Ask model for grounded synthesis or return safe refusal.

### Fintech example

- Classify a reported card purchase as dispute category.
- Extract transaction ID, amount, currency and date.
- Read get_transaction_status with permitted scope.
- Read get_dispute_policy for the approved rules.
- Prepare a dispute draft only after explicit policy check.
- Never let a schema-valid suggestion move money.

### Safety and reliability

- Use least-privilege read tools as the first integration.
- Separate informational tools from write operations.
- Block account changes without approval and policy.
- Apply argument validation before network requests.
- Retry transient errors only; dedupe side effects.
- Handle ambiguous classification with human review.

### Evaluate the runtime

- JSON schema acceptance and missing-field rates.
- Correctness of labels against a golden set.
- Precision of extracted amounts, dates and identifiers.
- Tool choice accuracy and argument validity.
- Unauthorized tool request rejection rate.
- Duplicate-side-effect count and p95 latency.

### Build and exercise

- Create extractor and classifier with fixed schemas.
- Register payment, merchant and policy lookup tools.
- Implement tool dispatcher with typed handlers.
- Add fake provider and deterministic test fixtures.
- Test missing fields, malformed JSON and denied tools.
- Demonstrate an auditable chargeback walkthrough.

### Exit checklist

- Explain structure versus semantic correctness.
- Version schemas and document their consumers.
- Validate arguments and tool outputs.
- Enforce policy before any side effect.
- Distinguish retryable from permanent failure.
- Deliver Tool Runtime v1, tests and example records.

## Hands-on training schedule

- **Monday:** Review **Key distinctions** and **Schema essentials**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Tool anatomy** and **Full execution path**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Full execution path** and **Fintech example**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Fintech example** and **Safety and reliability**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Evaluate the runtime** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- Classify a reported card purchase as dispute category.
- Extract transaction ID, amount, currency and date.
- Read get_transaction_status with permitted scope.
- Read get_dispute_policy for the approved rules.
- Prepare a dispute draft only after explicit policy check.
- Never let a schema-valid suggestion move money.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
