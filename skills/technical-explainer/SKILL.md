---
name: technical-explainer
description: Story-driven knowledge explanation, article writing, source-article/paper interpretation, and revision. Use when asked to write an educational article, blog, tutorial or thoughtful essay; explain, teach, analyze, or retell an existing article/paper/report so the reader can understand its reasoning; or improve the narrative of technical material. Lead readers through a concrete puzzle, exploration, evidence, mechanism and limits, without inventing facts. Especially useful for AI/ML, iOS, backend and software-engineering topics; can also adapt to evidence-based general knowledge writing.
metadata:
  version: "0.6.0"
---

# Technical Explainer — Story-Driven Knowledge Explanation

## Goal

Create source-faithful, accurate, and memorable explanations by letting the reader follow how an understanding is formed. Treat writing and article explanation as methods of testing understanding, not just producing polished text. **Storytelling here means a causal learning journey, not fictional plot or emotional decoration.**

## Story-first mode and task routing (v0.6.0)

The default teaching strategy for **writing an article** or **explaining someone else's article** is story-driven reasoning. Read [story-driven-explanation.md](references/story-driven-explanation.md) for the detailed arc, source-grounding requirements, short-answer adaptation, and examples.

**Select the work mode before applying the workflow:**

- **CREATE — original article or essay:** Build one coherent reader journey: an observable situation or puzzle → fair initial hypothesis/alternative → evidence or actual constraint → new understanding/mechanism → verification and boundary. The arc is a planning model, **not** compulsory section headings. Use the author's previously established topic and tone. For reflective nonfiction, never invent personal experiences. When creating a blog with illustrations, preserve the full-text author approval gate below.
- **EXPLAIN — interpret an existing paper, blog or report:** First access and accurately understand the source, including the authors' actual question, methods, claims, evidence and limitations. Only then reorder it around the reader's likely questions and deliver a clear narrative; explicitly separate author claims, explanatory metaphors, independent inference, and unverified assertions. Distinguish idea/prototype/measurement/production deployment. **Do not require the authoring approval gate or a figure plan just to explain an existing text.** If the source cannot be fully read, disclose what is verified.
- **REVISE — polish or restructure supplied text:** Repair broken reasoning, missing premises and out-of-order concepts before improving style. Preserve claims and voice unless correctness requires a transparent correction.
- **QUICK ANSWER / STRICT FORMAT:** For short questions, use a miniature arc (puzzle → useful distinction → answer) without padding. If the user explicitly requests a list, direct answer, contract comparison, code reference, exact technical spec or other non-narrative structure, honor it; storytelling must not obstruct retrieval or verification.

**Narrative truth constraints:**

1. Start with a real reader difficulty, not a contrived failure of an actually viable alternative; let a surprising truth be the turning point when appropriate.
2. Each section must change what the reader can now infer; move from known input to visible action, observed result and next useful question. A story without a causal handoff is still a glossary.
3. Use one recurring example when it helps. Label hypothetical scenes and toy computations; do not turn fictional stories, invented motives or imagined conversations into source history.
4. Preserve primary-source numbers, conditions, dates, and negative results. Clarify what evidence shows and what it cannot prove; when a source is involved, cite it at important claims.
5. Avoid mandatory heroes, three-act theater, melodrama, formulaic rhetorical questions and artificial cliffhangers. The reader should remember **why the mechanism works**, not merely its metaphor.
6. Adapt narrative density to task length, stakes and audience; for safety-critical or formal work, explicit criteria, risks and instructions outrank narrative flow.

## Workflow

### 1. Locate the article in its knowledge system (CREATE when part of a series)

- Identify the prior article's central problem, result, and reusable concept.
- Identify this article's one main problem and what the reader must learn.
- Clarify how the next topic could naturally emerge from an open question.
- Distinguish a *teaching sequence* from literal chronological or architectural evolution. Never assert that a newer architecture is simply the older one plus a component unless technically true.

### 2. Derive from the problem

Use the following **optional** causal scaffold, revising its shape to match the truth:
1. A concrete case exposes a meaningful question.
2. A plausible existing method or reader hypothesis is considered fairly.
3. Explain what it actually achieves and which real constraint, evidence or surprising fact matters; if it works, say so.
4. Introduce the mechanism, choice or insight that addresses the remaining question.
5. Verify with the smallest relevant example, source observation or experiment.
6. State the limits and next question.

Avoid term-first sections unless they are necessary for understanding.

**Causal justification is not the same as a forced necessity claim.** Before saying that a design is needed, ask whether the reader's simpler alternative would in fact work.

- If an alternative is viable, explicitly acknowledge it first, then compare the real constraints (e.g. implementation simplicity, representations, performance, batch interfaces, correctness, or maintainability). Do not invent an impossibility just to make the next technique seem inevitable.
- Distinguish **a mathematical requirement**, **an architectural choice**, and **a conventional engineering implementation**. A teaching sequence showing a reasonable choice does not prove it was the only possible solution.
- Trace actual data roles before claiming something “participates in computation”: identifiers/indices may select data, targets may index classes, learned vectors may enter matrix operations, and model parameters may receive gradients. Do not call a lookup index an input feature merely because it is numeric.
- Use the author's “why not do the obvious thing?” question as a mandatory review of the explanatory premise. Revise the preceding rationale if it was false; do not merely append a disclaimer after the original incorrect motivation.

### 3. Verify the difficult concepts before drafting

- Identify up to three likely misconceptions or reasoning bottlenecks.
- For each, choose a worked example, counterexample, simple computation, or small runnable program.
- Explicitly distinguish *learned parameters*, *per-input data*, and *temporary/internal state* where applicable.
- Ask for author explanation/rephrasing when collaborating; if the user has already signaled understanding or asks to proceed, do not force another approval round.

### 4. Make a figure-by-figure outline (only when planning figures for an authored article)

For every planned section, specify:
- Reader question
- Logical conclusion
- Diagram purpose (one learning obstacle per figure)
- What must be exact (arrows, labels, units, formulas)

Do not generate a large batch of diagrams before the key mechanism and article structure are stable. For actual figure creation, auditing, approval, or packaging, hand off each figure's brief to `technical-diagram` (when available); keep the article-level narrative and figure placement here.

### 5. Draft natural prose

- Use one connected argument instead of a glossary.
- Prefer small concrete examples before notation; introduce formulas only when they add explanatory value.
- Avoid self-congratulatory conclusions, unnatural transitions, and repetitive rhetorical questions.
- Keep caveats proportional. Examples illustrate common uses; do not falsely state exclusivity (e.g., CNN only images, RNN only text).
- If the reader's core question remains unanswered, revise before polishing tone.

### Mandatory full-text approval gate before image generation for authored articles

Figure planning and actual image creation are separate stages.

- During outlining, it is fine to record a **text-only figure plan**: the reader question, the paragraph it may support, and the intended teaching point. This is planning, not permission to generate.
- Before any image-generation or image-editing call, present the **complete article text** to the author for holistic review. Complete text includes the title, every section and paragraph, formulas, worked examples, transitions, figure references/captions where applicable, and the conclusion.
- Iterate on the prose until the author explicitly confirms the full-text context/version. A request to “continue” while drafting, approval of an outline, or approval of one section is not approval of the complete article.
- Before this approval, previews must be text-only. Do not create image candidates, edit figures, or insert unapproved images into a preview and ask the author to judge them without the full article context.
- After approval, freeze or identify the approved text version, then finalize figure briefs against that exact version and hand off to technical-diagram for generation, audit, and author approval.
- If later prose edits materially change a figure's teaching point, numbers, labels, order, or surrounding argument, pause the affected figure work and reconfirm the changed text context before revising the image.
- A figure brief may be drafted earlier in plain text, but **no actual image generation starts before full-text approval**.

### Delivery format: choose by actual handoff needs

- Do not generate a ZIP by habit; deliver Markdown, a single HTML preview, individual images, or a ZIP according to the actual task.
- A ZIP is permitted when multiple files need coordinated delivery, directory structure matters, or the author asks for one. It is not required for every article.
- Do not silently replace an author's requested output format; verify delivery is accessible in the user's client.
### AI03 case: Token ID is an index, not a neural-network feature (2026-11-02)

When explaining why a Token ID is used, do **not** assert “Token must participate in large amounts of numerical computation, so it must be turned into an integer.” The downstream matrix operations work on Embedding/hidden-state vectors, not on the literal Token text or its integer ID.

- Start with the viable alternative: a string-keyed table can retrieve the very same Embedding vector.
- Explain the common integer ID mapping as a **discrete lookup interface**: Token → stable vocabulary index → row in the Embedding parameter matrix. During language-model training, the target ID may also select the correct vocabulary class for Loss; neither use makes it a continuous Q/K/V input.
- Explain separately why an Embedding vector is useful: an arbitrary ID has no inherent continuous linguistic geometry; the learnable vector is what participates in subsequent attention and other neural-network computations.
- Clarify benefits narrowly: compact integer sequences, batched embedding gather, consistent vocabulary indexing at input and output. Do not claim that swapping string-keyed lookup for ID lookup changes Transformer expressivity, or that a GPU mathematically requires a Token ID.
- **Counterfactual acceptance check**: if a string dictionary and an integer-indexed matrix return identical vectors for each position, the downstream Transformer receives the same numerical inputs and can compute the same result. If the prose says otherwise, repair the causal chain.

In the referenced article, this correction belongs in the opening Token ID / Embedding section, **not** as an unrelated footnote at the end. See [tests 11–12](../../evals/technical-explainer.md) for regression scenarios. This case is validated as an identified error and corrected explanation in author collaboration, **not** yet validated through unfamiliar-reader or cross-topic testing.

### 6. Validate and revise

Check technical correctness, reader comprehension, figure logic, cross-article linkage, and the transition to the next topic. Use [writing-checklist.md](references/writing-checklist.md). After the author raises a new question, map the misunderstanding to the right section and update both prose and relevant figure rather than treating it as an unrelated Q&A.

## Collaborative reasoning before drafting (validated in Tokenization discussion, 2026-10-29)

When the author is learning the topic as part of writing, use **co-reasoning**, not a one-way lecture or a forced Q&A exam:

- Start from one concrete puzzle; define the variables and baselines before presenting a calculation. Invite the author to infer the next step, but if they cannot follow the example, **stop the quiz and repair the missing premise**.
- Treat repeated “I still don't understand” as diagnostic data, not a request for more volume. Identify whether the obstacle is an undefined concept, two quantities being confused, a missing counterexample, or a changed variable. Explain that exact gap with the smallest before/after comparison; then return to the thread.
- Explicitly distinguish **the total number of entries in a vocabulary** from **the number of tokens used to encode one string** (the Tokenization case). More generally, keep *resource capacity* and *per-input workload* distinct; fix other conditions when comparing costs.
- When the author's reasoning is partly correct, preserve the supported claim and revise only the false inference; distinguish hypothetical arithmetic, actual experimental output, and unverified claims. An experiment on a toy distribution is not proof of production behavior.
- After the author reconstructs the causal chain, promote their real questions into article acceptance checks and diagram briefs. Record the misunderstanding, the corrective example, and the specific section it changes. Do not quote the discussion wholesale as an article.
- Ask at most one useful understanding check at a time, and do not insist on an answer after the author indicates understanding or asks to move on.
- Prefer **discussion → minimal test → joint interpretation → prose → figure review** where the author is learning the topic. This ordering is conditional; it does not require every already-understood article to become a dialogue.

See [tokenization-coauthoring-case.md](references/tokenization-coauthoring-case.md) for the observed failure modes, successful repairs, and evidence limitations.

## Artifacts

For an EXPLAIN request, the normal deliverable is a **standalone explanation of the provided source**: the real problem, initial intuition, substantive mechanism, evidence/limitations and transferable implications. Do not turn a user's request to understand an article into a publishing workflow. For CREATE, use [article-outline.md](assets/article-outline.md) where appropriate; for both modes, use [story-driven-explanation.md](references/story-driven-explanation.md) and [writing-checklist.md](references/writing-checklist.md).

Depending on the requested stage, produce a topic thesis, diagram-aware outline, section sample, full draft, diagram briefs, or revision notes. Do not repeatedly reconfirm a previously approved outline. Use [article-outline.md](assets/article-outline.md) when a structure is needed.

## Concrete worked example

See [rnn-case-study.md](references/rnn-case-study.md) for a real understanding gap involving RNN parameter sharing.

## Semantic image naming (2026-11-01)

- Do not put editorial sequence numbers such as `图01`, `图02`, or `Figure 3` on the image canvas, in asset filenames, or in article captions/references.
- Name image assets by stable subject, e.g. `parameter-update.png`, `shared-vs-independent-weights.png`, or `training-vs-inference.png`. Do not encode article position or display order in the filename.
- The Markdown document determines display order through the location of each image reference. Inserting, deleting, or moving one image must not require renaming other assets or changing their paths.
- Track candidate/final status, revision, source provenance, and SHA-256 in the article plan or manifest, not through ordinal filenames. Use descriptive identifiers when multiple assets address related topics.
- Preserve numbers that carry actual technical meaning, such as time steps, layer indices, sequence positions, dimensions, or measured values.

## Additional rules validated during RNN V2

### Explain mechanism with verifiable computation
- When claiming that a mechanism enables memory, feature extraction, or context modeling, explicitly demonstrate the computation that produces the effect. Do not stop at a definition or an abstract formula.
- Use the smallest numerical example or runnable code that demonstrates the effect; trace intermediate values and validate arithmetic.
- Clearly mark deliberate simplifications (e.g. omission of nonlinearity and bias). Distinguish exact computational traceability from the difficulty of interpreting learned semantic representations.
- If the writer's real questions reveal a missing logical step after V1, restructure the draft at that step rather than appending unrelated extra content.

### Editorial numbering versus delivered image file names

- Do not use editorial sequence numbers in the canvas, asset filename, article caption, or Markdown reference. Use a stable semantic filename and let Markdown placement determine display order.
- When adding, removing, or reordering figures, update only the relevant Markdown insertion point and its descriptive manifest entry; do not rename unrelated image assets.
- Keep revision status, source provenance, and content hashes in the plan/manifest. Do not use figure numbers as identity or provenance.
- Preserve meaningful technical numbers such as time steps, sequence positions, dimensions, layer indices, and measured values.
- An image primarily exists to explain one concrete point. Prefer correct arrows, indices, shapes and simple labels over text-heavy decorative diagrams.
## Additional rules validated during Transformer outline and sections 1–2 (2026-10-13)

### Progressive depth without mandatory formula-first exposition
- For a technically literate reader new to the subject, introduce the concrete problem and information flow **before** symbols or large equations. A reader's math background is a constraint on presentation, not a reason to remove technical accuracy.
- Distinguish **author-side verification** from **reader-facing exposition**: the writer should check numerical examples, dependencies, and diagram arrows, but the main narrative can show a verified mechanism with a small diagram and ordinary language. Put optional step-by-step arithmetic in an appendix when it would interrupt the argument.
- Avoid two opposite failures: merely naming a mechanism without showing how it acts, and front-loading derivations before the reader knows what question they answer.
- Use a single recurring example to link adjacent sections, with each section answering the question left open by the previous one. Introduce at most the necessary new terms at each step.
- Apply a relevance filter to intermediate technologies: mention them briefly if needed for accuracy, but avoid teaching an entire side architecture when the article's core question does not depend on it. Example: LSTM/GRU may be acknowledged without a gate-by-gate lesson in a Transformer introduction.
- This is a **conditional technique**, not a prohibition on mathematics. Use formulas prominently when they are central to the reader's goal, and keep the underlying calculation available for audit.

## Additional rules distilled from Transformer FFN explanation review (2026-10-16)

### Explain the next component with a visible handoff, not a new label

- **Check explanatory slope before naming a mechanism.** Start with a concrete example the reader already understands. State what the previous component has produced, show the remaining question, then introduce what the next component *does to that output*. Name the component after its role is intelligible.
- **Do not explain unfamiliar jargon with different unfamiliar jargon.** A phrase such as "position-wise nonlinear feature transformation" is a useful technical label *after* explanation, not a self-sufficient explanation of why FFN is present. First show input, action, and output in ordinary language; then map those steps to precise terms.
- **Favor a visible work handoff:** previous step → its output → next useful operation → next step's output. A simple everyday analogy may convey the process faster than a premature proof or formula. The analogy should be discarded or qualified where it misstates what the components can actually do.
- **Separate workflow intuition, architectural motivation, and mathematical necessity.** Showing what a component contributes does not prove the architecture cannot work without it. Do not fabricate an exclusive deficiency in the previous component merely to justify the next one.
- **Preserve boundaries while staying readable.** Example: "Attention lets token positions gather information; FFN processes each position's current representation" is a helpful first-pass mental model. It does **not** mean Attention cannot transform features, FFN performs semantic reasoning alone, or Attention-only networks are necessarily linear and incapable of learning complex relationships.
- **React to comprehension feedback, not just text polish.** If the author repeatedly says "I still don't understand why it exists," reconsider the question and explanatory order. More definitions, formulas, or an unrelated example may increase cognitive load without closing the causal gap. Offer the smallest connected illustration first, and deepen only where the remaining question genuinely requires it.

**Editorial checkpoint:** For each new module, can the reader answer (1) What did the last step actually output? (2) What new operation is useful next? (3) What goes in and comes out? (4) Which parts of the explanation are teaching metaphors rather than factual capability limits?

**Evidence scope:** This guidance is distilled from author feedback comparing multiple FFN explanations. The easier-to-follow *explanation pattern* was identified; this does not establish that the author's underlying technical uncertainty is fully resolved, nor does it mandate one analogy for all articles.

## Plain-language-first exposition for algorithm beginners (2026-10-16)

### Reader baseline and narrative slope

- **Treat readers and the author as beginners in algorithms/ML unless the specific concept has already been established**, even if they have years of software-development experience. Programming experience is not assumed knowledge of vectors, neural networks, projections, gradients, or model training.
- **Everyday situation → concrete remaining question → plain-language operation → name the technique → only the necessary technical detail.** Do not begin with a glossary, a technical definition, or a formula.
- **One unfamiliar concept at a time.** Before writing any sentence with two or more unfamiliar terms, rewrite it so the reader can picture the action using already established concepts. When a term becomes necessary, define it in a short everyday sentence at first use.
- **Use a process the reader can follow.** Carry the same example across modules; say what happened *before*, what actually happens *during*, and what changes *after*. Show the useful input and output, not just arrows connecting boxes or role labels.
- **Plain words first, precision in a light second layer.** Put implementation details, optional mathematics, exception cases, and lengthy technical caveats in a short aside or optional appendix when they interrupt the main storyline. Do not omit correctness; avoid misleading absolutes and add one focused qualification where the analogy could otherwise be wrong.
- **Analogies must help, not legislate capabilities.** An analogy such as "Attention is a meeting; FFN is processing your notes afterward" is useful for the handoff, but does not prove that Attention never transforms representations or that FFN alone understands relationships. Never claim attention-only systems are necessarily linear, that particular heads have fixed semantic jobs, or that an example number is a real learned attention weight.
- **Test for cognitive load:** After each paragraph, ask whether an algorithm beginner can explain in ordinary words what new action just happened *without needing to learn another term first*. If not, simplify the explanation or postpone the detail instead of adding definitions.
- **Keep diagrams equally beginner-friendly:** visually mark starting information, the action, and the result. Prefer one clear causal change over many arrows, attention weights, labels, and decorative components on one canvas.

### Editorial acceptance test

A draft passes this style check when someone unfamiliar with algorithms can answer: **What was the problem? What did we try? What changed after this step? Why is the next step useful?** If the author says an explanation remains difficult, treat that as a failed comprehension test and revise the *explanatory sequence*, not merely its vocabulary.

This is a reader-facing **default**, not a ban on technical detail: mathematical rigor and source checks remain mandatory in author-side validation, and mathematics belongs prominently in the article when it is the actual subject.
