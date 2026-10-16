---
name: technical-explainer
description: Write or revise problem-driven technical educational articles, tutorials, and blog series. Use when the user wants to explain a technical concept from first principles, connect it to a previous article, develop an outline, create a complete draft, plan supporting diagrams, or revise text after understanding gaps are discovered. Particularly suited to AI/ML/software engineering topics.
metadata:
  version: "0.5.0"
---

# Technical Explainer

## Goal

Create technically sound, understandable explanations by working backward from the reader's concrete question. Treat writing as a method for testing understanding, not just producing polished text.

## Workflow

### 1. Locate the article in its knowledge system

- Identify the prior article's central problem, result, and reusable concept.
- Identify this article's one main problem and what the reader must learn.
- Clarify how the next topic could naturally emerge from an open question.
- Distinguish a *teaching sequence* from literal chronological or architectural evolution. Never assert that a newer architecture is simply the older one plus a component unless technically true.

### 2. Derive from the problem

Structure the reasoning as:
1. A concrete case exposes a problem.
2. A plausible existing method is tried.
3. Explain precisely where it falls short.
4. Motivate the new mechanism.
5. Verify its behavior with a minimal example.
6. State the limits and next question.

Avoid term-first sections unless they are necessary for understanding.

### 3. Verify the difficult concepts before drafting

- Identify up to three likely misconceptions or reasoning bottlenecks.
- For each, choose a worked example, counterexample, simple computation, or small runnable program.
- Explicitly distinguish *learned parameters*, *per-input data*, and *temporary/internal state* where applicable.
- Ask for author explanation/rephrasing when collaborating; if the user has already signaled understanding or asks to proceed, do not force another approval round.

### 4. Make a figure-by-figure outline

For every planned section, specify:
- Reader question
- Logical conclusion
- Diagram purpose (one learning obstacle per figure)
- What must be exact (arrows, labels, units, formulas)

Do not generate a large batch of diagrams before the key mechanism and article structure are stable.

### 5. Draft natural prose

- Use one connected argument instead of a glossary.
- Prefer small concrete examples before notation; introduce formulas only when they add explanatory value.
- Avoid self-congratulatory conclusions, unnatural transitions, and repetitive rhetorical questions.
- Keep caveats proportional. Examples illustrate common uses; do not falsely state exclusivity (e.g., CNN only images, RNN only text).
- If the reader's core question remains unanswered, revise before polishing tone.

### 6. Validate and revise

Check technical correctness, reader comprehension, figure logic, cross-article linkage, and the transition to the next topic. Use [writing-checklist.md](references/writing-checklist.md). After the author raises a new question, map the misunderstanding to the right section and update both prose and relevant figure rather than treating it as an unrelated Q&A.

## Artifacts

Depending on the requested stage, produce a topic thesis, diagram-aware outline, section sample, full draft, diagram briefs, or revision notes. Do not repeatedly reconfirm a previously approved outline. Use [article-outline.md](assets/article-outline.md) when a structure is needed.

## Concrete worked example

See [rnn-case-study.md](references/rnn-case-study.md) for a real understanding gap involving RNN parameter sharing.

## Additional rules validated during RNN V2

### Explain mechanism with verifiable computation
- When claiming that a mechanism enables memory, feature extraction, or context modeling, explicitly demonstrate the computation that produces the effect. Do not stop at a definition or an abstract formula.
- Use the smallest numerical example or runnable code that demonstrates the effect; trace intermediate values and validate arithmetic.
- Clearly mark deliberate simplifications (e.g. omission of nonlinearity and bias). Distinguish exact computational traceability from the difficulty of interpreting learned semantic representations.
- If the writer's real questions reveal a missing logical step after V1, restructure the draft at that step rather than appending unrelated extra content.

### Editorial numbering versus delivered image file names
- **Inside images:** never place editorial figure numbering such as "图1", "图2", or "Figure 3" on the canvas. Keep actual time-step numbers such as "第1步", "t=1" when they carry technical meaning.
- **For delivered image files:** always name illustrations in article order using **`图01-简短主题.png`, `图02-简短主题.png`**, etc. Use zero-padded two-digit indices so file sorting works for ten or more images. Descriptive themes should be concise.
- Store the ordinal in the filename and article caption/reference layer, not in the artwork, so graphics can be reused in other articles.
- When adding, removing, or reordering figures, update impacted image filenames, Markdown image paths and ZIP/delivery manifest together; confirm that every referenced file exists.
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
