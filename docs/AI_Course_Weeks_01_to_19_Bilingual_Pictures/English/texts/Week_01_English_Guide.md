# Week 01 — LLM Runtime & Prompt / Context Engineering

**Focus:** Responses API, provider abstraction and a governed fintech application

**Expected deliverable:** A working LLM Runtime v1 with repeatable prompts, structured request/response records and a safe demo.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **Business question** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Request validation** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Context assembly** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Policy check** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **OpenAI / Bedrock** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **Response verification** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **Audit and metrics** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### Core concepts

- LLM runtime = the application layer around a model.
- A model is not an application, workflow or system of record.
- Messages, roles and instructions shape each invocation.
- Responses API is one way to call a model consistently.
- OpenAI and Amazon Bedrock are alternative provider paths.
- Keep provider-specific details behind one adapter.

### Prompt engineering

- Separate system, developer and user instructions.
- Define task, scope, output, tone and prohibited actions.
- Use clear delimiters for quotes and retrieved documents.
- Few-shot examples show expected behavior without proving truth.
- Ask for uncertainty and missing evidence explicitly.
- Test prompts on representative fintech inputs.

### Context engineering

- Select only relevant data, definitions and policies.
- Arrange stable instructions before changing case context.
- Include currency, time window and business definitions.
- Treat retrieved text as data, not new authority.
- Do not put credentials or unnecessary personal data in prompts.
- Track context source, freshness and access rights.

### Architecture

- HTTP/API facade validates the incoming request.
- AuthN/AuthZ binds user, purpose and allowed domain.
- Context builder fetches authorized fintech information.
- Model gateway routes to provider and records usage.
- Output checker enforces schema and safety constraints.
- Telemetry captures latency, tokens and errors.

### Fintech example

- User asks for a card-chargeback explanation.
- Read only the authorized dispute metadata.
- Retrieve applicable definitions and evidence.
- Request an explanation, not an account mutation.
- Return concise facts, sources and uncertainty.
- Require human approval for any sensitive action.

### Safety and governance

- Minimize PII before sending external requests.
- Whitelist tools and enforce role-based access.
- Disclose model uncertainty without inventing balances.
- Log request ID, prompt version and model identifier.
- Use timeouts and explicit retry decisions.
- Do not let generated text bypass business policy.

### Measurements

- Task success on a small golden question set.
- Latency p50/p95 and timeout count.
- Input/output tokens and cost per request.
- Groundedness and factual support where relevant.
- Schema-valid response rate when structure is required.
- Safety violations and missing-evidence rate.

### Build and exercise

- Implement LLM Runtime v1 in TypeScript.
- Create provider interface and a fake local provider.
- Create three prompts for concrete fintech tasks.
- Add context builder, logging and response checks.
- Compare responses with and without trusted context.
- Record a runnable end-to-end demo.

### Exit checklist

- Explain prompts versus context engineering.
- Use correct role priority and delimiters.
- Demonstrate provider interchangeability.
- Show authorized, minimally sufficient context.
- Return errors without fabricated facts.
- Deliver README, sample outputs and test evidence.

## Hands-on training schedule

- **Monday:** Review **Core concepts** and **Prompt engineering**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Context engineering** and **Architecture**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Architecture** and **Fintech example**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Fintech example** and **Safety and governance**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Measurements** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- User asks for a card-chargeback explanation.
- Read only the authorized dispute metadata.
- Retrieve applicable definitions and evidence.
- Request an explanation, not an account mutation.
- Return concise facts, sources and uncertainty.
- Require human approval for any sensitive action.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
