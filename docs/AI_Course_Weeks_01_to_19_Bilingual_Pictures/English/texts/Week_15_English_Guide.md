# Week 15 — Semantic Layer, Knowledge Graph & GraphRAG

**Focus:** Give agents an authorized map of enterprise entities, relationships and evidence paths

**Expected deliverable:** A governed enterprise context graph connecting certified metrics, systems, owners, events and deployments.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **Enterprise sources** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Metadata ingestion** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Entity resolution** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Ontology + graph** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Hybrid graph/document retrieval** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **Evidence paths** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **Grounded answer** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### Semantic foundations

- Semantic layer defines shared business meaning.
- Ontology defines valid entity and relation types.
- Knowledge graph stores specific nodes and edges.
- Property graphs support labeled relation properties.
- RDF represents subject-predicate-object triples.
- GraphRAG retrieves connected facts and evidence paths.

### Fintech graph entities

- Domain, system, component and API.
- Kafka topic, schema, producer and consumer.
- Dataset, certified metric and business term.
- Owner, deployment, rule set and incident.
- Merchant, payment, transaction and chargeback.
- Each node needs stable identity, sensitivity and source.

### Reliable ingestion

- Ingest catalog from Backstage / Khatu-X.
- Load definitions and lineage from Collibra / metadata.
- Read approved datasets and views from Snowflake.
- Read MSK topics and schema registry relationships.
- Link GitLab deployments with Datadog operational signals.
- Store provenance, revision, freshness and confidence.

### Entity resolution

- Normalize naming variants without merging unrelated IDs.
- Use canonical identifiers and curated aliases.
- Match deterministic references before fuzzy similarity.
- Flag low-confidence merges for human verification.
- Maintain identity history and provenance.
- Avoid broken lineage from duplicate service nodes.

### Evidence-path retrieval

- Detect entities mentioned in the question.
- Resolve canonical nodes and permission scopes.
- Traverse only valid and relevant relation types.
- Build metric-to-dataset-to-system-to-deploy paths.
- Combine graph with vector and keyword evidence.
- Return compact citations, timestamps and uncertainties.

### Chargeback investigation

- Start from certified chargeback_rate definition.
- Follow calculation to chargeback and payment datasets.
- Link the producing payments service and Kafka topic.
- Inspect connected fraud rules and recent deployments.
- Correlate timing with actual observed operational signals.
- A connected path suggests investigation, not proven causality.

### Access and observability

- Filter nodes, edges and properties before retrieval.
- Enforce domain, tenant and sensitivity policies.
- Hide internal fraud rules from unauthorized users.
- Log graph query, path count and filtered entities.
- Measure evidence coverage and graph freshness.
- Audit every claim back to permitted source records.

### Build and exercise

- Define fintech ontology and relationship rules.
- Ingest sample catalog, metrics and deployments.
- Implement graph store and alias resolution.
- Query multi-hop paths with policy filters.
- Create GraphRAG retriever and evidence formatter.
- Run scenarios with missing, conflicting and denied data.

### Exit checklist

- Distinguish semantic layer, graph and GraphRAG.
- Demonstrate valid ontology and deduplicated nodes.
- Trace an evidence path across enterprise systems.
- Combine graph and document retrieval safely.
- Enforce property-level restrictions and citations.
- Deliver documented graph, tests and lineage demo.

## Hands-on training schedule

- **Monday:** Review **Semantic foundations** and **Fintech graph entities**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Reliable ingestion** and **Entity resolution**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Entity resolution** and **Evidence-path retrieval**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Evidence-path retrieval** and **Chargeback investigation**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Access and observability** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- Detect entities mentioned in the question.
- Resolve canonical nodes and permission scopes.
- Traverse only valid and relevant relation types.
- Build metric-to-dataset-to-system-to-deploy paths.
- Combine graph with vector and keyword evidence.
- Return compact citations, timestamps and uncertainties.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
