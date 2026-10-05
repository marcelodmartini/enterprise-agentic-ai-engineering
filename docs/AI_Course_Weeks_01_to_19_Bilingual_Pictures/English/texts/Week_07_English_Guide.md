# Week 07 — MCP, Remote Tools & Deferred Tool Loading

**Focus:** Expose enterprise capabilities to agents with discovery, schemas and permissions

**Expected deliverable:** A controlled tool catalog and MCP-style integration with dynamic discovery and policy enforcement.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **User intent** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Tool search** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Load matching descriptor** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Validate schema and scope** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Remote tool call** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **Verify response** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **Trace and cite** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### MCP mental model

- Model Context Protocol standardizes tool/resource access.
- Client connects to a server exposing capabilities.
- Tools execute operations; resources provide readable context.
- Descriptions and schemas document allowed inputs.
- Discovery finds relevant capabilities without guessing.
- MCP is a protocol boundary, not a security exemption.

### Catalog and discovery

- Store short names, descriptions and tags for search.
- Match user intent to candidate tools and domains.
- Load full descriptors only for selected candidates.
- Keep tool schema and version in a registry.
- Make ownership, side effects and cost visible.
- Avoid sending every enterprise tool into each prompt.

### Deferred tool loading

- Start with a small indexed tool catalog.
- Select and authorize relevant tool names first.
- Fetch complete schema only when a tool is needed.
- Reduce prompt tokens and incorrect tool choices.
- Cache safe descriptors by version and tenant scope.
- Invalidate descriptors when authorization changes.

### Remote execution

- Validate inputs against strict JSON Schema.
- Bind caller, tenant, purpose and allowed resources.
- Use service-to-service auth and request timeouts.
- Run read-only queries before sensitive operations.
- Normalize typed results, errors and provenance.
- Never trust tool output as a higher-priority prompt.

### Fintech example

- Search for a certified chargeback metric tool.
- Discover read-only Snowflake or Collibra endpoint.
- Load schema for date, domain and merchant filters.
- Run authorized query and capture source details.
- Return results with owner and freshness context.
- Escalate any action tool requiring approval.

### Security boundary

- Use allowlists, ABAC/RBAC and scoped credentials.
- Separate MCP tool discovery from permission to execute.
- Do not expose raw credentials or unrestricted SQL.
- Apply schema, rate, cost and data-volume limits.
- Treat remote prompts/resources as untrusted content.
- Audit caller, tool name, arguments class and outcome.

### Signals to measure

- Tool discovery precision and missed-tool rate.
- Descriptor tokens saved by deferred loading.
- Argument validation and permission-denial counts.
- Tool p95 latency, availability and retry rate.
- PII exposure tests and unsafe action attempts.
- End-to-end task accuracy with selected tools.

### Build and exercise

- Create a short searchable tool catalog.
- Implement deferred descriptor fetch and cache.
- Expose payment, policy and merchant read tools.
- Validate schema and domain authorization.
- Simulate remote tool errors and offline server.
- Demonstrate discovery-to-result with complete trace.

### Exit checklist

- Distinguish client, server, resource and tool.
- Explain registry versus semantic tool search.
- Load only relevant descriptors at runtime.
- Enforce permissions independently of the agent.
- Handle tool errors without invented answers.
- Deliver catalog, adapters, tests and security notes.

## Hands-on training schedule

- **Monday:** Review **MCP mental model** and **Catalog and discovery**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Deferred tool loading** and **Remote execution**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Remote execution** and **Fintech example**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Fintech example** and **Security boundary**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Signals to measure** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- Search for a certified chargeback metric tool.
- Discover read-only Snowflake or Collibra endpoint.
- Load schema for date, domain and merchant filters.
- Run authorized query and capture source details.
- Return results with owner and freshness context.
- Escalate any action tool requiring approval.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
