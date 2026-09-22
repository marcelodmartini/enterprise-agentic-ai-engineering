# Week 06 — LangGraph, Workflows, Agents & Human Review

**Focus:** Design controlled agentic processes with state, checkpoints and approval gates

**Expected deliverable:** A graph-based fintech case workflow with bounded agent steps and a formal human pause.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **Case request** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Initialize graph state** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Retrieve evidence** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Analyze with agent** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Policy branch** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **Human gate when needed** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **Draft and audit** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### Agent versus workflow

- A workflow specifies known steps and business transitions.
- An agent may select steps dynamically within a boundary.
- Agentic workflows combine stable control with flexible analysis.
- Graph nodes are activities; edges encode transitions.
- Graph state holds case, evidence and status.
- Business policy, not model text, authorizes actions.

### Graph design

- Define typed input, output and graph state.
- Each node has one responsibility and clear contract.
- Use conditional edges for risk and missing evidence.
- Set maximum tool calls and iteration limits.
- Persist checkpoints at meaningful transition points.
- Keep nondeterministic model calls in isolated activities.

### Durability basics

- Persist state so a restart need not restart the case.
- Checkpoint results, completed tools and approvals.
- Avoid repeating a financial side effect on replay.
- Version graph, prompt, tool and policy resources.
- Use event history for debugging and audit.
- Differentiate a pause from an error or cancellation.

### Human-in-the-loop

- Pause before a high-impact irreversible action.
- Present evidence, risk, proposed action and alternatives.
- Allow approve, reject or request-more-information.
- Record reviewer identity, time and decision reason.
- Use expiration and escalation for pending reviews.
- Resume only after validation of signed authorization.

### Fintech scenario

- Open a card-chargeback investigation.
- Retrieve payment, merchant and policy evidence.
- Use agent to draft an evidence-based explanation.
- Policy branches high-risk cases to human review.
- On approval, prepare a draft case with an idempotent key.
- Record final result without automatically promising reversal.

### Policies and safeguards

- Separate read tools from transactional write tools.
- Enforce scoped permissions per graph node.
- Bound recursion, tokens, tools and time.
- Use guardrails on user input and tool output.
- No undocumented model-directed side effects.
- Block if critical policy or evidence is unavailable.

### Quality and telemetry

- Step-level success and failure counts.
- Workflow completion, pause and rejection rates.
- Approval latency and stuck-case count.
- Tool accuracy and unnecessary call count.
- Checkpoint recovery and duplicate-side-effect count.
- Quality of grounded final drafts.

### Build and exercise

- Model a case as graph nodes and conditional edges.
- Implement typed state, transitions and fake tools.
- Add policy branches and an approval interrupt.
- Persist checkpoint and simulate process restart.
- Test invalid transitions, rejection and replay.
- Document the graph and its human decision gates.

### Exit checklist

- Explain workflow versus agent tradeoffs.
- Show typed state and bounded agent steps.
- Resume from a saved checkpoint safely.
- Prevent duplicate business side effects.
- Demonstrate a logged approval/rejection path.
- Deliver graph workflow, tests and architecture map.

## Hands-on training schedule

- **Monday:** Review **Agent versus workflow** and **Graph design**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Durability basics** and **Human-in-the-loop**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Human-in-the-loop** and **Fintech scenario**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Fintech scenario** and **Policies and safeguards**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Quality and telemetry** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- Open a card-chargeback investigation.
- Retrieve payment, merchant and policy evidence.
- Use agent to draft an evidence-based explanation.
- Policy branches high-risk cases to human review.
- On approval, prepare a draft case with an idempotent key.
- Record final result without automatically promising reversal.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
