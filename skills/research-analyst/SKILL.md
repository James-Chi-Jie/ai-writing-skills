---
name: research-analyst
description: Investigate and critically evaluate existing technical papers, research articles, engineering proposals, software architecture claims, benchmarks and viral technology reports. Use when the user asks what a paper or technical article really contributes, how it compares with existing approaches, whether evidence proves claimed gains, or why it is attracting attention. Start from primary sources, baseline audits and prior art; communicate conclusions only after evaluation.
metadata:
  version: "0.1.0"
---

# Research Analyst — Evidence before presentation

## Goal

Give an **independent, calibrated judgment** about an existing body of work. Do not treat a fluent summary of authors' architecture as evaluation. Research is not an exercise in justifying a previously chosen story.

Read [research-review-checklist.md](references/research-review-checklist.md) for the detailed gate. Use [analysis-outline.md](assets/analysis-outline.md) when a structured research artifact is needed. Presentation can use [shared storytelling](../../shared/communication/storytelling.md) **after** the evidence review; the narrative is optional.

## Trigger and scope

Use for: “这篇文章讲什么、重要在哪、有没有新东西”、论文解读、技术行业热议的创新性分析、方案与竞品比较、benchmark 审查、研究启发和局限。 If the user simply asks for a definition, derivation, learning tutorial, or explanation of an already identified mechanism, **handoff to** [technical-explainer](../technical-explainer/SKILL.md). A single user request can need sequential Skills: research the paper first, then teach one difficult concept.

Do **not** apply academic novelty audits mechanically to contract reconciliation, creative prose, or every casual question. Expand rigor proportionally to the strength of the claim and impact of a wrong conclusion.

## Research workflow

1. **Frame the question and audience.** Distinguish a request for faithful summary, innovation assessment, reproducibility review, engineering adoption decision, or trend/virality analysis. Honor the user's existing expertise; if they know Supervisor/Worker, don't spend most of the output introducing it.
2. **Acquire reliable sources.** Prefer primary author text, published paper/version, official design docs, implementation and complete experiment setup. If only abstract/excerpts are accessible, name the limits. For rapidly changing subjects, verify dates and recency.
3. **Extract testable claims.** Record problem, proposed mechanisms, claims of novelty, actual prototype/production status, evidence, metrics, negative outcomes and author-declared limitations. Don't equate author's motivation with established fact.
4. **Check prior art and the strongest plausible alternative.** Search the closest public approaches, confirming dates and comparable feature scope. Separate **old architectural idea**, **new combination/engineering packaging**, **actual new mechanism**, and **forward-looking proposal**. Do not invent an innovation deficit or novelty for dramatic effect.
5. **Audit the experiment.** Inspect whether each baseline really used the capability being compared; model/prompt/tool setup, sample size, task distribution, controls, variability, budget and metric definitions. Correct numbers with a weak comparator can still support a misleading headline.
6. **Quantify costs alongside gains.** Compare latency/quality/completion, total read/write Token, execution and supervision costs, safety/recovery and human attention as applicable. Don't infer global superiority from a single metric.
7. **Calibrate conclusions.** Deliver a concise top-line verdict, then an evidence-backed distinction among **demonstrated, plausible, speculative, and unknown**. Cite primary sources near specific claims. When asked “why is it viral,” separate measured attention from hypothesized causes.
8. **Communicate appropriately.** Use a table, comparative narrative, or story only if it helps. Source facts, teaching analogies and assistant deductions must be distinguishable. Close with what practical lesson is transferable and what further evidence would change the conclusion.

## Evidence integrity / failure checks

- Never compare against a “multi-Agent” baseline without checking that it actually delegated to agents in the tested runs.
- When task execution is simulated, explicitly limit conclusions to the simulated aspect (e.g., coordination or scheduling); do not claim real code quality gains.
- A prototype, a public reference implementation and a production deployment are different maturity levels.
- “Everyone is discussing it” is not evidence of technical novelty.
- Avoid false equivalence: a predecessor may share a high-level idea while differing substantially in task model, event subscription or persistence.
- Cite what supports each claim; do not imply you read an unavailable source. Clearly name uncertainty.

## Handoff graph

- Need a **reader-friendly derivation of a verified specific mechanism**? Hand off to [technical-explainer](../technical-explainer/SKILL.md), preserving the evidence boundaries and verified facts from this review.
- Need diagrams for an **authored article**? Teaching/article owner uses [technical-diagram](../technical-diagram/SKILL.md) after the author's confirmed full-text approval. A source review alone does not authorize image creation.
- Need attractive prose? Apply [shared storytelling](../../shared/communication/storytelling.md) as a presentation aid without changing the research verdict.

## Evaluation

Use [research-analyst evals](../../evals/research-analyst.md). Re-run counterexamples whenever research process rules are changed. New tests are not automatically a proof of cross-topic effectiveness.
