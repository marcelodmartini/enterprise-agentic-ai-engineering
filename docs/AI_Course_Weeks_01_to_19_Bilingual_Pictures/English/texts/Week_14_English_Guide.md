# Week 14 — AI Governance, Risk, Compliance & Model Risk

**Focus:** Demonstrate that each AI system is inventoried, validated, approved and continuously monitored

**Expected deliverable:** AI Governance v1 with inventory, risk tiering, evidence packages and audit-ready release decisions.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **Register AI system** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Assess impact / risk** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Map controls** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Collect evidence** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Independent review** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **Approve or remediate** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **Monitor and audit** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### Governance foundation

- Inventory agents, prompts, models and business use cases.
- Assign business and technical owner to every system.
- System card states purpose, limits, users and data.
- Risk tiers account for impact, autonomy and reversibility.
- Governance produces evidence rather than assurances.
- Apply proportional control depth to system risk.

### Reference frameworks

- NIST AI RMF: Govern, Map, Measure, Manage.
- ISO/IEC 42001: organizational AI management system.
- EU AI Act: risk categories and context-specific duties.
- Bank model risk practices: validation and monitoring.
- Applicability depends on jurisdiction and exact use case.
- Use frameworks as references, not automatic legal clearance.

### Risk and controls

- Assess customer, financial and data impacts.
- Evaluate external exposure and automated authority.
- Map security, privacy, quality and operations controls.
- Require strong checks for credit, fraud and blocking.
- Record exceptions, mitigation owner and expiry.
- Reassess risk when use case or autonomy changes.

### Evidence package

- Keep system card and architecture diagram.
- Include data lineage, model and prompt version.
- Attach eval report and red-team / security results.
- Record privacy review and policy-control mapping.
- Preserve approvals, monitoring snapshot and changes.
- Link each item to source, owner, date and hash.

### Independent validation

- Review conceptual design and intended use.
- Check data representativeness and evaluation protocol.
- Test hallucination, grounding and tool correctness.
- Verify human review, retention and leakage controls.
- Document limitations and open validation findings.
- Approvers must be independent when policy requires it.

### Release decision path

- Compare risk tier with required controls.
- Block release if mandatory evidence is missing.
- Reject unresolved high/critical findings.
- Capture explicit approver roles and decisions.
- Publish approved revision and deployment conditions.
- Send rejected systems to owned remediation workflow.

### Continuous governance

- Monitor quality, drift, incidents and overrides.
- Revalidate after material model or prompt change.
- Audit who accessed data and authorized actions.
- Track findings from open to independently closed.
- Report relevant exceptions and release history.
- Protect audit records from unauthorized modification.

### Build and exercise

- Create registry of eight illustrative fintech AI systems.
- Assign owners, autonomy levels and risk tiers.
- Map controls and compile evidence for each.
- Simulate validation failures and missing approvals.
- Implement governance orchestrator and audit log.
- Produce a reviewed release or remediation report.

### Exit checklist

- Demonstrate current inventory and system cards.
- Show risk rationale and proportional controls.
- Produce a traceable evidence package.
- Record independent validation and approvers.
- Monitor and reopen findings after change.
- Deliver audit-ready governance review.

## Hands-on training schedule

- **Monday:** Review **Governance foundation** and **Reference frameworks**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Risk and controls** and **Evidence package**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Evidence package** and **Independent validation**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Independent validation** and **Release decision path**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **Continuous governance** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- Review conceptual design and intended use.
- Check data representativeness and evaluation protocol.
- Test hallucination, grounding and tool correctness.
- Verify human review, retention and leakage controls.
- Document limitations and open validation findings.
- Approvers must be independent when policy requires it.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
