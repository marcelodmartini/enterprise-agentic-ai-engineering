# Week 04 — Embeddings, Chunking, Ingestion & Vector Search

**Focus:** Turn approved documentation into a searchable retrieval corpus

**Expected deliverable:** Retriever v1 with versioned documents, metadata filters, vector search and evaluation queries.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **Approved sources** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Parse and normalize** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Chunk + metadata** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Create embeddings** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Index vectors** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **Authorized search** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **Relevant chunks** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### Retrieval fundamentals

- Retrieval selects information relevant to a question.
- Embeddings map text into numeric semantic vectors.
- Similarity scores rank related meanings, not truth.
- Keyword and semantic retrieval solve different problems.
- Top-k sets the number of candidates returned.
- Vector proximity is not proof or source certification.

### Good corpus design

- Choose authoritative approved policies and runbooks.
- Remove duplicates and superseded document versions.
- Keep document title, owner, date and source URI.
- Classify sensitivity, tenant, domain and access scope.
- Record ingestion version and freshness timestamps.
- Do not embed raw secrets or unnecessary PII.

### Chunking strategies

- Split by headings and semantic boundaries first.
- Use manageable token length and limited overlap.
- Keep definitions next to relevant exceptions.
- Record documentId, chunkId and section offset.
- Avoid chunks combining unrelated policy versions.
- Compare fixed-size, paragraph and structural chunks.

### Ingestion architecture

- Load approved document and verify provenance.
- Parse, normalize and redact restricted information.
- Create chunks and metadata, then embed.
- Upsert idempotently into vector index.
- Track index, embedder and content versions.
- Reindex and delete when source permissions change.

### Vector search path

- Validate user purpose and permitted domains.
- Embed the query with the compatible model.
- Apply metadata and policy filters before ranking.
- Retrieve candidates with scores and source IDs.
- Remove duplicates and stale versions.
- Return chunks as evidence candidates, not final answers.

### Fintech example

- Index certified dispute policies and chargeback FAQs.
- Search for evidence about reversal conditions.
- Filter by product, country and policy version.
- Display document owner and effective date.
- Compare results for exact IDs and conceptual questions.
- Escalate when the corpus does not cover a case.

### Quality and controls

- Recall@k on labeled relevant-document queries.
- Precision@k and first relevant result position.
- Index freshness and missing metadata rate.
- Unauthorized document exposure rate.
- Embedding/storage cost and retrieval latency.
- Detect poor chunk boundaries in failed queries.

### Build and exercise

- Create Retriever v1 with parser and chunker.
- Build deterministic sample embeddings or real adapter.
- Store vectors and metadata in an index.
- Implement top-k cosine-similarity retrieval.
- Write quality tests for ten fintech questions.
- Inspect relevance failures and revise chunk design.

### Exit checklist

- Explain embeddings versus keyword matching.
- Trace every retrieved chunk to its source.
- Enforce metadata permissions and freshness.
- Tune chunk length, overlap and top-k on evidence.
- Show evaluation data and failed cases.
- Deliver index, retriever code and documented corpus.

## Hands-on training schedule

- **Monday:** Review **Retrieval fundamentals** and **Good corpus design**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Chunking strategies** and **Ingestion architecture**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Ingestion architecture** and **Vector search path**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Vector search path** and **Fintech example**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Quality and controls** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- Validate user purpose and permitted domains.
- Embed the query with the compatible model.
- Apply metadata and policy filters before ranking.
- Retrieve candidates with scores and source IDs.
- Remove duplicates and stale versions.
- Return chunks as evidence candidates, not final answers.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
