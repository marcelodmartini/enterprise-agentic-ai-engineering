# Week 05 — RAG, Grounding, Hybrid Search & Reranking

**Focus:** Answer fintech questions from auditable evidence rather than plausible text

**Expected deliverable:** A citation-first RAG service that blends retrieval, reranks evidence and abstains when necessary.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **Question** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Permission and intent** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Keyword + vector search** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Merge and rerank** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Evidence filter** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **LLM answer** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **Citation and policy audit** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### What RAG does

- Retrieval-Augmented Generation adds external context.
- The retriever finds source material for the model.
- Grounding links each material claim to that evidence.
- Citations identify document, section and version.
- A missing source requires uncertainty, not invention.
- RAG reduces some errors but does not guarantee truth.

### Hybrid retrieval

- Keyword/BM25 captures exact policy names and IDs.
- Vector search captures paraphrases and semantics.
- Fuse scores or rank lists into candidate pool.
- Filter by tenant, product, date and access policy.
- Deduplicate repeated excerpts across documents.
- Tune retrieval with labeled fintech questions.

### Reranking and selection

- Reranker evaluates query-to-chunk relevance.
- Consider authority, recency and source certification.
- Use top-k retrieval, then smaller evidence set.
- Prefer complete provisions over isolated sentences.
- Avoid mixing conflicting effective policy versions.
- Keep source IDs attached through every stage.

### Grounded answer design

- Give model only authorized, selected evidence.
- Specify question, permitted scope and citation form.
- Distinguish facts, interpretation and missing data.
- Return source pointers for each key assertion.
- Abstain or ask for review when evidence conflicts.
- Validate output format and cite actual retrieved IDs.

### Fintech walkthrough

- Question: Why was a dispute classified this way?.
- Find exact dispute code plus equivalent wording.
- Rerank certified policy and merchant case notes.
- Identify effective version for transaction date.
- Compose explanation with references and caveats.
- Do not declare fraud or promise a refund.

### Security and governance

- Retrieved instructions are untrusted content.
- Filter permissions before inserting retrieved chunks.
- Mask PII, retain audit of evidence selection.
- Block unsupported sensitive actions.
- Use document revocation and cache invalidation.
- Record retriever, reranker and prompt versions.

### Useful evaluation

- Answer faithfulness / citation support.
- Context precision and recall@k.
- Correctness of exact ID and date matching.
- Abstention behavior when sources are absent.
- Latency of retrieve, rerank and generate.
- Cost per grounded and accepted answer.

### Build and exercise

- Implement lexical and vector retrieval adapters.
- Merge and rerank candidates with version filters.
- Create citation-aware answer builder.
- Construct known-answer and no-answer test cases.
- Compare vector-only versus hybrid outcomes.
- Ship end-to-end RAG demo with evidence trail.

### Exit checklist

- Describe where grounding evidence comes from.
- Trace every answer claim to retrieved sources.
- Handle contradictions and absent documents safely.
- Validate hybrid and reranking with an eval set.
- Keep policy enforcement outside the model.
- Deliver citation-first RAG service and reports.

## Hands-on training schedule

- **Monday:** Review **What RAG does** and **Hybrid retrieval**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Reranking and selection** and **Grounded answer design**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Grounded answer design** and **Fintech walkthrough**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Fintech walkthrough** and **Security and governance**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Useful evaluation** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- Question: Why was a dispute classified this way?.
- Find exact dispute code plus equivalent wording.
- Rerank certified policy and merchant case notes.
- Identify effective version for transaction date.
- Compose explanation with references and caveats.
- Do not declare fraud or promise a refund.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
