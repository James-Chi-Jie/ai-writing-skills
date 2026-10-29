# Diagram Acceptance and Provenance Checklist

Use this during every image review and again before full-article packaging.

## Review record

| Field | Required value |
| --- | --- |
| Figure ID / teaching question | Article position and the one learning obstacle |
| Source | Exact original filename and location; attach/open the actual image |
| Source digest | SHA-256 of the actual bytes, when file access permits |
| Visual reference | Author-approved source image/style and date or link |
| Technical contract | Input → action → output, arrows, constraints, verified example |
| Candidate | Exact file and digest, revision number |
| Review | Technical pass/fail; visual pass/fail; article alignment pass/fail |
| Author status | planned / candidate / needs-revision / author-confirmed / published |
| Delivery | Final PNG filename, Markdown reference, platform preview status |

Never change status to `author-confirmed` based solely on “继续”, “可以，继续”, or success of file checks.

## Technical review

- [ ] Every arrow represents a real dependency, access, sequence, or clearly labeled analogy.
- [ ] Inputs, outputs, stages, temporal order, and actor boundaries are correct.
- [ ] No impossible future-position access or misplaced caching/streaming stage.
- [ ] All mathematical values, labels, indices, units, dimensions, and example text are checked.
- [ ] Illustrative values/2D layouts are not represented as measured facts.
- [ ] Permitted beginner simplifications do not generate a fundamental false mental model.
- [ ] Figure and current article use the same example, terminology, and intended depth.

## Image role and failed-generation recovery
- [ ] Identify cover/hero vs. body explanatory figure and record its section, exact question, and permitted content.
- [ ] A body figure does not expand into an article-wide poster, regardless of article title.
- [ ] All figures use checked inputs and numbers; no invented measured tokens or unrelated panels.
- [ ] A scope failure was rejected, with its cause diagnosed **before** a retry.
- [ ] The retry substantively changed allowed layout/content and exclusions; if it failed again, unconstrained generation stopped.
- [ ] Rejected figures were not silently converted to cover art, archived, or called approved; a text mockup was not mislabeled a generated PNG.

## Visual review
- [ ] Compare the **rendered actual image** to the author's chosen visual reference.
- [ ] No conflicting goals (minimal single diagram versus poster/formula/multi-panel overload).
- [ ] Chinese text, punctuation, numbers, formula signs, and arrows are accurate and readable.
- [ ] No clipping/overlap; legible at intended width and on a narrow screen.
- [ ] One figure answers one question; no unnecessary next-section mechanisms.
- [ ] Editorial figure index appears in filename/caption, not on the canvas.

## Teaching hierarchy and visual-density review
- [ ] Main heading describes the reader-visible **outcome**; mechanism belongs in the explanatory layer.
- [ ] A trade-off graphic shows benefit, cost, meaningful boundary/counterexample, and a concise takeaway when all are relevant to one question.
- [ ] Design type fits the task (two-case contrast, mechanism sequence, measured-data table, or trade-off); no forced four-panel layout.
- [ ] Clear typographic hierarchy, aligned cards, purposeful color and readable chips—not an austere form or a crowded poster.
- [ ] Visual preference is separated from technical validity; every number/segmentation/latency inference independently checked.
- [ ] If the preferred candidate has incorrect facts, retain its useful layout while removing unsupported data; do not count visual approval as numerical verification.

## Approval and packaging review

- [ ] One clearly identified candidate was shown; any revision is traceable to that source.
- [ ] Exact approved file and digest are recorded; do not silently regenerate or replace.
- [ ] Confirmed figure IDs map one-to-one to final filenames, captions and Markdown paths.
- [ ] Final render uses approved pixels, not a different plausible-looking version.
- [ ] ZIP/paths/CRC verification and technical/visual/author acceptance are distinct checks.
- [ ] Do not publish or change repository status until the author approves the actual assembled article.
