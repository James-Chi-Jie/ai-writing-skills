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

## Visual review

- [ ] Compare the **rendered actual image** to the author's chosen visual reference.
- [ ] No conflicting goals (minimal single diagram versus poster/formula/multi-panel overload).
- [ ] Chinese text, punctuation, numbers, formula signs, and arrows are accurate and readable.
- [ ] No clipping/overlap; legible at intended width and on a narrow screen.
- [ ] One figure answers one question; no unnecessary next-section mechanisms.
- [ ] Editorial figure index appears in filename/caption, not on the canvas.

## Approval and packaging review

- [ ] One clearly identified candidate was shown; any revision is traceable to that source.
- [ ] Exact approved file and digest are recorded; do not silently regenerate or replace.
- [ ] Confirmed figure IDs map one-to-one to final filenames, captions and Markdown paths.
- [ ] Final render uses approved pixels, not a different plausible-looking version.
- [ ] ZIP/paths/CRC verification and technical/visual/author acceptance are distinct checks.
- [ ] Do not publish or change repository status until the author approves the actual assembled article.
