---
name: technical-explainer
description: Write or revise problem-driven technical educational articles, tutorials, and blog series. Use when the user wants to explain a technical concept from first principles, connect it to a previous article, develop an outline, create a complete draft, plan supporting diagrams, or revise text after understanding gaps are discovered. Particularly suited to AI/ML/software engineering topics.
metadata:
  version: "0.1.0"
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
