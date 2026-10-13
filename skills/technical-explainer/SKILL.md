---
name: technical-explainer
description: Write or revise problem-driven technical educational articles, tutorials, and blog series. Use when the user wants to explain a technical concept from first principles, connect it to a previous article, develop an outline, create a complete draft, plan supporting diagrams, or revise text after understanding gaps are discovered. Particularly suited to AI/ML/software engineering topics.
metadata:
  version: "0.3.0"
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
