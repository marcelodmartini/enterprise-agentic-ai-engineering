# Week 03 — Prompt Caching, Conversation State & Memory

**Focus:** Build a stateful, cost-aware fintech assistant without losing important context

**Expected deliverable:** Stateful Chat v1 with durable history, scoped memory, compaction and cache-aware prompts.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **User turn** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Identity and session** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Load relevant state** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Compose cache-friendly prompt** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Model response** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **Verify** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **Save turn and compact** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### Four separate layers

- The model holds no durable business state by itself.
- Conversation state stores the current dialogue and steps.
- Long-term memory stores selected reusable information.
- Compaction summarizes old turns to fit context limits.
- Prompt caching reuses repeated input prefixes.
- State, memory, cache and source-of-truth data differ.

### State design

- Use conversationId, tenantId, userId and requestId.
- Persist ordered turns with timestamps and roles.
- Record workflow step and pending human decisions.
- Store prompt, policy and model versions.
- Track history ownership, retention and deletion.
- Keep financial balances in the authorized source system.

### Cache-aware context

- Place stable system instructions at the beginning.
- Keep tool definitions and stable schemas consistent.
- Append variable case facts and user turns afterward.
- Measure cached-input tokens and cache hit rates.
- Invalidate stale or permission-sensitive cache entries.
- Never share private cache content across tenants.

### Memory and compaction

- Write only relevant and justified durable memories.
- Store provenance, scope and expiry with each item.
- Summarize decisions, unresolved questions and citations.
- Preserve explicit user constraints in compacted summaries.
- Remove redundant chatter, not authoritative evidence.
- Audit what was retained, shortened or discarded.

### Fintech example

- Analyst asks repeatedly about one dispute case.
- Restore prior steps and which tools were already called.
- Retrieve current transaction status from the source.
- Reuse stable dispute-policy instructions from cache.
- Compact old discussion without losing approval status.
- Return a grounded next step with continuity.

### Privacy and policy

- Classify personal data before memory persistence.
- Apply role and tenant filters on memory retrieval.
- Encrypt storage and avoid secret logging.
- Set TTL and right-to-delete workflows where applicable.
- Do not infer permission from conversation history.
- Revalidate live facts rather than trusting remembered values.

### Measure and validate

- Context token growth across long sessions.
- Cache hit and cost reduction over repeated turns.
- Memory retrieval relevance and factual consistency.
- State restoration after a restart.
- Compaction preservation of critical constraints.
- Cross-user data leakage rate must remain zero.

### Build and exercise

- Implement session store and typed conversation state.
- Create cache-friendly prompt composer.
- Add memory selection and relevance rules.
- Implement summary-based compaction with audit.
- Simulate long conversations and process restart.
- Test tenant isolation and stale context invalidation.

### Exit checklist

- Explain state versus long-term memory.
- Show safe persistence and scoped retrieval.
- Resume a conversation without losing key decisions.
- Measure caching and compaction behavior.
- Keep authoritative fintech facts in core systems.
- Deliver Stateful Chat v1 and traceable examples.

## Hands-on training schedule

- **Monday:** Review **Four separate layers** and **State design**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Cache-aware context** and **Memory and compaction**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Memory and compaction** and **Fintech example**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Fintech example** and **Privacy and policy**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Measure and validate** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- Analyst asks repeatedly about one dispute case.
- Restore prior steps and which tools were already called.
- Retrieve current transaction status from the source.
- Reuse stable dispute-policy instructions from cache.
- Compact old discussion without losing approval status.
- Return a grounded next step with continuity.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
