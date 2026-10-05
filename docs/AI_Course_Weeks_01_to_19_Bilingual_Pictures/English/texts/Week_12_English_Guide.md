# Week 12 — Fine-Tuning, Multimodal, Voice & Computer Use

**Focus:** Select specialized model and interface techniques with fintech-grade controls

**Expected deliverable:** A controlled multimodal automation prototype with evaluation, voice safety and computer-action policy.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **Document / voice / screen input** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Validate consent and format** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Specialized AI step** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Policy / evidence** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Human gate** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **Scoped action** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **Audit** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### Fine-tuning decisions

- Fine-tuning adapts model behavior using labeled examples.
- It is not a replacement for live RAG or source retrieval.
- Start from a baseline and measurable failure class.
- Curate authorized, diverse and reviewed training examples.
- Use held-out tests for regressions and subgroup gaps.
- Consider prompting, routing and distillation first.

### Multimodal inputs

- Images support document and receipt understanding.
- Audio supports transcription and spoken interaction.
- Video and screen input may add operational context.
- Validate quality, format, consent and payload limits.
- Keep visual evidence and extracted fields traceable.
- Do not infer identity or ownership from a model guess.

### Realtime voice

- Speech input may be transcribed or processed in-session.
- Manage latency, interruptions and turn-taking.
- Disclose AI interaction where appropriate.
- Confirm sensitive facts with clear read-back steps.
- Require secondary authentication for protected requests.
- Escalate when confidence or authorization is insufficient.

### Computer use

- Agent operates an approved UI only within scope.
- Use screenshots as untrusted data, not commands.
- Allowlist permitted screens, clicks and fields.
- Require human approval for submit, payment or blocking.
- Record snapshots and action evidence for audit.
- Use API integration when it is safer and available.

### n8n and orchestration

- Compose deterministic business workflow around AI nodes.
- Keep credentials and secrets in secure integrations.
- Validate each webhook and tool input/output schema.
- Separate informational automations from write operations.
- Add retry, dead-letter and manual escalation paths.
- Version workflow definitions and test failure branches.

### Fintech walkthrough

- Customer uploads a dispute receipt photo.
- Validate image and extract merchant, date and amount.
- Cross-check extracted fields against transaction data.
- Use AI to draft an evidence-based case summary.
- Reviewer approves any sensitive case submission.
- Archive permitted evidence, decision and trace.

### Safety and evaluation

- Measure field extraction precision and missing rates.
- Benchmark voice latency and ASR error by environment.
- Detect wrong UI target and unauthorized actions.
- Minimize biometric, image and audio retention.
- Test prompt injection hidden in documents/screens.
- Never let low model confidence trigger unsafe action.

### Build and exercise

- Create fine-tuning dataset and baseline comparison.
- Prototype structured image-to-field extraction.
- Simulate realtime voice session and interruptions.
- Implement computer-use action policy and audit.
- Build a deterministic n8n-style workflow spec.
- Run multimodal and policy regression tests.

### Exit checklist

- Know when fine-tuning is appropriate or unnecessary.
- Use RAG for changing authoritative facts.
- Gate voice, image and UI actions with consent/policy.
- Demonstrate safe human handoff.
- Show evaluation and traceable evidence.
- Deliver multimodal prototype and safety report.

## Hands-on training schedule

- **Monday:** Review **Fine-tuning decisions** and **Multimodal inputs**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Realtime voice** and **Computer use**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Computer use** and **n8n and orchestration**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **n8n and orchestration** and **Fintech walkthrough**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Safety and evaluation** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- Compose deterministic business workflow around AI nodes.
- Keep credentials and secrets in secure integrations.
- Validate each webhook and tool input/output schema.
- Separate informational automations from write operations.
- Add retry, dead-letter and manual escalation paths.
- Version workflow definitions and test failure branches.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
