# Week 08 — AI Evaluations, Judges, Regression & MLflow

**Focus:** Replace subjective demos with repeatable quality measurements and release decisions

**Expected deliverable:** An evaluation harness with golden data, multiple scorers, regression comparison and experiment tracking.

## The complete visual learning path

The diagram follows these stages, in sequence. Each stage has an explicit responsibility and must preserve authorization and evidence where applicable.

1. **Golden cases** — Record the relevant inputs, outputs, decisions and errors at this boundary.
2. **Candidate version** — Record the relevant inputs, outputs, decisions and errors at this boundary.
3. **Deterministic checks** — Record the relevant inputs, outputs, decisions and errors at this boundary.
4. **Judge rubric** — Record the relevant inputs, outputs, decisions and errors at this boundary.
5. **Human sample** — Record the relevant inputs, outputs, decisions and errors at this boundary.
6. **Baseline comparison** — Record the relevant inputs, outputs, decisions and errors at this boundary.
7. **Report / release gate** — Record the relevant inputs, outputs, decisions and errors at this boundary.

## Detailed reference notes (all English infographic text)

### Evaluation taxonomy

- Offline evals compare candidates on a frozen dataset.
- Online evals sample approved production behavior.
- Human review checks ambiguous or high-impact outputs.
- Deterministic scorers test schemas, exact values and policy.
- LLM judges assess semantic qualities with a rubric.
- Golden sets encode representative expected behavior.

### Good eval cases

- Record input, context, purpose and expected behavior.
- Include reference facts and authorized source IDs.
- Label negative, ambiguous and no-evidence examples.
- Cover product, risk group, language and edge cases.
- Record prompt, model, tool and dataset versions.
- Reserve held-out cases to reduce overfitting.

### Scorers and rubrics

- Use exact match only when exactness matters.
- Score citation support, completeness and factuality.
- Define ordinal rubrics and example judge decisions.
- Calibrate judge consistency with human reviewers.
- Separate task success from safety violation checks.
- Report disagreement and uncertain judgments.

### Regression control

- Save an approved baseline before a new version.
- Run both versions on the same cases and conditions.
- Compare per-category changes, not only average score.
- Block material safety or compliance regressions.
- Inspect failures and create focused regression fixtures.
- Do not change the benchmark to hide deterioration.

### Fintech cases

- Dispute reason classification and evidence summarization.
- Fraud warning that must not assert confirmed fraud.
- KYC with missing document or poor image.
- Collections content requiring compliance review.
- Query with no authorized or current evidence.
- Prompt injection and unauthorized tool attempts.

### Experiment tracking

- Track prompt, model, retrieval and tool versions.
- Save dataset version and scorer configuration.
- Store outputs, scores, latency and cost in MLflow.
- Compare runs with stable identifiers and metadata.
- Attach redacted artifacts and reviewer decisions.
- Preserve reproducibility without retaining unnecessary PII.

### What to measure

- Task success, extraction accuracy and label F1.
- Groundedness and citation correctness.
- Policy violation and sensitive data leakage.
- Tool choice correctness and argument validity.
- Latency, token usage and cost per passed case.
- Regression count by severity and business domain.

### Build and exercise

- Construct 30+ varied and labeled fintech cases.
- Implement schema, exact and rubric-based scorers.
- Run baseline and candidate over identical inputs.
- Create report with changes and concrete failures.
- Log experiments and artifacts to MLflow.
- Gate a sample deployment on critical metrics.

### Exit checklist

- Distinguish deterministic, model and human judges.
- Define rubric and golden-data ownership.
- Demonstrate reproducible candidate comparison.
- Detect significant domain-specific regression.
- Keep safety failures separate from quality average.
- Deliver eval harness, report and tracked runs.

## Hands-on training schedule

- **Monday:** Review **Evaluation taxonomy** and **Good eval cases**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Tuesday:** Review **Scorers and rubrics** and **Regression control**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Wednesday:** Review **Regression control** and **Fintech cases**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Thursday:** Review **Fintech cases** and **Experiment tracking**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Friday:** Review **What to measure** and **Build and exercise**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.
- **Saturday:** Review **Build and exercise** and **Exit checklist**, then implement or test one observable, reproducible example. Capture its inputs, expected outcomes, allowed actions and failure behavior.

## Worked fintech scenario

- Dispute reason classification and evidence summarization.
- Fraud warning that must not assert confirmed fraud.
- KYC with missing document or poor image.
- Collections content requiring compliance review.
- Query with no authorized or current evidence.
- Prompt injection and unauthorized tool attempts.

## Verification and sign-off

Use the evaluation, security, operational and exit-checklist sections above as acceptance tests. Test positive, negative, missing-data and unauthorized cases. Record actual evidence rather than marking a capability complete because it appeared to work once.

## Coverage and fidelity note

This English companion reproduces every point written on the corresponding newly typeset English poster and organizes the week’s main curriculum concepts. It is a detailed English learning edition, not a literal page-by-page translation of the much longer Spanish source chapter or a pixel-identical replacement of the original artwork. The original illustrative diagrams also contained tiny, sometimes visually inconsistent lettering; the recreated diagrams use verified, editable English copy instead.
