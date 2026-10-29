---
name: technical-diagram
description: Plan, generate, revise, audit, and deliver accurate educational diagrams for technical blogs, tutorials, and AI/ML or software-engineering explainers. Use when an article needs a mechanism, data-flow, architecture, comparison, token/process, or numerical illustration; when reviewing a generated figure; or when assembling approved figures into an article. Enforce the author's chosen visual style, technical correctness, explicit approval, and source-file/version traceability.
---

# Technical Diagram

Create diagrams that help an algorithm beginner understand one real mechanism. A convincing-looking image is not evidence of technical correctness or author approval. Coordinate with `technical-explainer`: it owns the article's reasoning and figure placement; this skill owns a figure's visual brief, generation, review, approval, and delivery.

## Image role and scope gate (Tokenization lesson, 2026-10-29)

Before any generation, classify the asset explicitly:
- **Cover / hero:** represents the article's overall topic, with an independently approved cover brief.
- **Body explanatory figure:** belongs to one specific paragraph, answers one learning question, and depicts only the smallest necessary mechanism or controlled comparison.

Do not turn a planned body figure into a summary poster based on the article title or full draft. A body-figure generation brief must specify the exact allowed content (example, numbers, labels, layout), its article section, and excluded sections/panels. An article title is not authorization to create a cover.

### Mandatory recovery when a generated image misses the target

1. Mark the image **rejected / needs-revision**; identify the exact scope error and do not archive, publish or silently repurpose it as a cover.
2. Change the **substance** of the next generation task: one role, one teaching point, fixed validated example, explicit allowed layout and forbidden extra content. A rephrased version of the same broad prompt is not a meaningful correction.
3. Re-check the corrected brief against technical evidence. Do not add unsupported numbers, purported real tokenizer outputs or new panels merely for aesthetics.
4. Generate one corrected candidate and inspect the actual rendering. If it repeats the same scope failure, **stop unconstrained regeneration** and report the blocker or switch to a constrained edit/layout method.
5. A text-card sketch or UI mockup shown to explain the target is not a generated or approved PNG; identify it as a mockup.

**Regression example:** Tokenization article figure 01 is a two-case toy comparison: vocabulary A has `pro`, `gram`, `ming` (3 entries), so encoding `programming` uses 3 Tokens; B adds `programming` (4 entries), so the same string uses 1 Token. The generated eight-panel and six-panel article summaries were both rejected. They do not become covers or approved figures by default.

## Required inputs and decision record

Before generating, establish a figure record:
- **Teaching question:** the one reader confusion this figure resolves, its article paragraph, and what the reader should infer afterward.
- **Mechanism contract:** actual inputs, transformation, output, actors, sequence, arrows, symbols, boundaries, checked numbers, and prohibited implications.
- **Simplification boundary:** what is an illustration rather than a measured model fact; which causal/temporal constraints may never be simplified away.
- **Visual contract:** author-selected reference image, layout, color, typography, aspect ratio, language, density, and export format. A confirmed reference outweighs generic aesthetic suggestions.
- **Provenance:** exact source filename/image, candidate version, author feedback, and approval state. For previously approved figures, retrieve the original rather than reconstructing it from a description.

If a crucial reference or approved file is unavailable, ask for it. Do not claim to have seen or preserved a missing original. Never infer approval from an ambiguous message.

## Workflow and quality gates

### 1. Brief before generation

1. Write a one-sentence teaching question and the minimal before → action → after sequence.
2. List labels, values, arrows, constraints, and the exact article example. Reuse the article's terminology and scenario.
3. Remove material belonging to the next figure: supplementary formulas, new modules, poster-style knowledge summaries, and competing subplots.
4. Reconcile the prompt: do not simultaneously require a simple single-purpose image and a multi-panel formula-heavy poster. If the user already selected a visual reference, use it consistently.

**Gate A — Pedagogy:** one main learning obstacle; the reader can tell what changed and why.

### 2. Validate the technical model

- Check actor and layer boundaries, directions, chronology, dependency, indices, dimensions, units, formula values, and input/output state. Trace examples manually or with computation when feasible.
- Distinguish demonstrated facts from toy values, analogies, and inferred behavior. Label illustrative attention weights or 2D embeddings as illustrative; do not call them measured.
- For causal/autoregressive diagrams, test whether any edge accesses future positions or implies a forbidden dependency.
- Preserve simplified explanations for beginners only when they do not invert the mechanism or create a fundamental misconception. Move deeper detail to a later article when appropriate.
- Use primary technical sources for contested facts and record the checked assumptions. Ask for clarification rather than inventing model-specific implementation details.

**Gate B — Correctness:** pass the mechanism contract before making a polished image.

### 3. Generate or revise one traceable candidate

- Default to **one candidate for one teaching question**; make multiple variations only on explicit request.
- Use the author's already accepted reference and requested file format. For James's current LLM blog series, the latest approved direction is pastel, rounded, modern flat educational illustration with clear Chinese hierarchy, small everyday objects, and PNG delivery. **Do not produce programmatic box-flowchart SVGs or deliver SVG for that series unless James explicitly changes the decision.** This preference is project-specific, not a universal ban on SVG.
- If revising an accepted visual, edit that same image with the smallest needed change. Never silently regenerate, substitute a new style, or use a new filename to hide a changed visual.
- Keep editorial numbering (e.g. `图01`) out of the canvas; preserve numbers that explain a real step or time index.

**Gate C — Visual:** verify the rendered candidate itself: actual Chinese characters, numerical text, arrows, legibility at article width/mobile, unclipped labels, layout, palette, and reference-style match. Do not rely on prompt text or successful export alone.

### 4. Review independently of generation

Use [the acceptance and provenance checklist](references/acceptance-and-provenance.md). Record specific findings as:
- **Blocker:** false causal relationship, impossible access, wrong output state, unverified numerical claim presented as fact, or wrong source image.
- **Revision:** ambiguous arrow, wrong/overfull label, style drift, poor readability, or mismatched article example.
- **Accepted simplification:** intentionally imprecise teaching shorthand that cannot create a fundamental misconception.

Show the candidate and concrete findings to the author. Fix blockers, then re-inspect the edited result. Do not mark a file complete merely because a renderer, ZIP CRC, path check, or mathematical check succeeds.

**Gate D — Author:** statuses are `planned` → `candidate` → `needs-revision` → `author-confirmed` → `published`. A reply such as “继续” or “可以，继续” authorizes the next action but **does not confirm the current image**. Record confirmation only when it identifies the specific visual/file, or after an explicit complete article-image acceptance.

### 5. Assemble, preserve, and deliver

- Maintain a manifest mapping article figure ID, exact source filename, content digest (prefer SHA-256), visual description, technical-review status, author-approval status, final filename, and Markdown path.
- Reuse the exact confirmed bytes. Before packaging, compare filename **and hash and actual visual** to the approved original; never replace a pure overview with a different three-layer engineering diagram simply because both are titled “图01”.
- When final order is known, name PNGs `图01-简短主题.png`, `图02-简短主题.png`, etc. Renaming does not permit changing visual content. Synchronize the manifest, figure numbers, captions, and Markdown references.
- Verify every referenced file exists and every image renders in the full article; independently confirm that those are the **approved versions**. File-integrity checks do not prove visual approval.
- If the user requested GitHub or publication updates, archive only confirmed artifacts and update actual publication state; never label a draft published or claim an unuploaded image is archived.

**Gate E — Provenance:** exact source ↔ approved visual ↔ final asset ↔ article reference must match.

## LLM diagram regression checks

Use these when relevant, not as universal depiction rules:
- Separate model computation / next-token generation from API streaming delivery. A streamed chunk is not guaranteed to equal one Token.
- Prefill is the model processing the existing context; do not label the entire API request and tokenizer path as Prefill. Decode extends the generated context, with new-token computation on each step.
- KV Cache is reused during generation, not a third phase after Decode; caching does not eliminate computation for a new Token.
- Avoid implying every model adds a fixed positional vector immediately after embedding; position handling varies.
- In causal attention, position 6 must not read positions 7–9. An illustrative weight is not a measured probability.
- Do not insert training as a mandatory step in a single inference call.

## Deliverables

At the requested stage, provide a figure brief, one candidate image, a succinct review table, or a final manifest plus article-ready PNG files. State unresolved blockers and exact approval status. Treat each actual user correction as a reusable regression test, not a reason to add vague style advice.
