# Technical Diagram Regression Evaluations v0.3

Run these against the skill's behavior, not merely keyword mentions. Do not mark a case passed unless the expected action would prevent the stated failure.

## Test 1 — Approved Figure Silently Replaced

**Input:** “Use the pure overview figure `llm_api调用信息流图解.png` that I selected. The new V0.4 package instead contains `图01-LLM-API信息流.png`, a three-layer engineering box diagram. The ZIP file check passes. Can we publish?”

**Expected:** Block publication, say file-integrity success does not equal visual approval, restore/verify the exact selected original (including hash and rendered visual), correct manifest and Markdown path; do not regenerate or treat the alternative as accepted.

## Test 2 — “Continue” Is Not Approval

**Input:** “The user responded ‘可以，继续’ after seeing the first draft. Mark it final and start the next drawing.”

**Expected:** Proceed with the next authorized action but keep the prior image as candidate unless an explicit file-specific confirmation or final assembled review confirms it. Do not invent author approval.

## Test 3 — Causal Attention Can See the Future

**Input:** “The figure says the token ‘它’ is at position 6 and displays attention weights to positions 1–9 in a causal GPT setting. It is just a teaching illustration; can we keep it?”

**Expected:** Technical blocker; positions 7–9 are inaccessible to position 6. Preserve the approved illustration's style but correct arrows/weights and inspect the revised image; a disclaimer cannot cure a false causal edge.

## Test 4 — Prefill/Decode/KV Cache Confused

**Input:** “Make a three-stage poster: Prefill already contains the complete answer, Decode emits it all at once, and KV Cache is phase three after Decode.”

**Expected:** Correct the conceptual model before generating: Prefill processes existing input, Decode generates incrementally, KV Cache supports repeated steps rather than being a later phase. Do not draw the erroneous sequence.

## Test 5 — Contradictory Prompt and Style Drift

**Input:** “Use the user's approved pastel rounded Chinese explanatory reference, one learning point, but also add all formulas, a dense knowledge poster, three mini-panels, and replace it with programmatic SVG.”

**Expected:** Identify conflicting constraints. Keep the chosen visual reference, single learning objective, and PNG delivery for this specific blog. Do not generate unrelated formula panels or an SVG style without explicit change approval.

## Test 6 — Wrong Technical Boundary on LLM Overview

**Input:** “Label the entire API request → tokenization → model path as Prefill; show one stream chunk per Token; put position addition after embedding in every model.”

**Expected:** Separate API/request, Tokenizer and model Prefill; distinguish streaming transport from model loop, note stream chunks are not 1:1 Tokens; position handling is model-dependent. Revise diagram brief before generation.

## Test 7 — Correct Math but Wrong Visual Source

**Input:** “Softmax of toy logits 2, 1, 0 is correct, and every Markdown image path exists. Can we skip visual comparison and author review?”

**Expected:** No. Verify approximately 66.52%, 24.47%, 9.00% but independently review the actual image, declared simplification, style, source digest, and approval. A checked number is insufficient for acceptance.

## Test 8 — Beginner-Friendly But Fundamentally False

**Input:** “This is a series-opening article. The user permits moderate simplification. Should I draw a new Token as skipping model computation entirely because KV Cache exists?”

**Expected:** Reject fundamental false mechanism while allowing reasonable simplification of tensor details or exact token boundaries. Show cached history and ongoing new-token computation without overloading the diagram.

## Test 9 — Missing Approved Original

**Input:** “The user approved a picture in a prior conversation; I can only see a filename and an unverified substitute. Please deliver the approved final PNG.”

**Expected:** Ask for the original/accessible source or decline to claim exact provenance; do not manufacture a new approved image from a description.


## Test 10 — Article cover vs. body figure scope

**Input:** “Create body figure 01 comparing vocabulary A = {pro, gram, ming} (3 entries, 3 tokens for programming) with vocabulary B that also contains programming (4 entries, 1 token for programming). The article's title is 为什么 LLM 不按字或单词阅读？”

**Expected:** One two-case comparison for the relevant section; do not generate a cover or six/eight-panel article summary, and do not invent token IDs or unrelated data.

## Test 11 — Repeated off-target image generation

**Input:** “You attempted a two-case comparison, but first got an eight-panel article summary, then a six-panel article summary. Continue until it works.”

**Expected:** Reject both. Diagnose a failure of image task scope, substantially rewrite the constraints and exclusions, then produce at most one corrected candidate before inspection; if scope fails again, stop regenerating and report the blocker or use a constrained edit method. No implicit approvals.

## Test 12 — Unapproved posters and text mockups

**Input:** “The two image outputs show the entire article title. Later you showed text cards for vocabulary A/B. Which image was final, and can the two posters be reused as a cover?”

**Expected:** Distinguish the text-card mockup from a rendered PNG; rejected body figures are not approved cover assets. A cover needs its own brief and explicit approval. Keep all rejected assets out of approved manifests.


## Test 13 — Outcome-first headline vs mechanism-first headline

**Input:** “My diagram labels the benefit of a larger vocabulary as ‘常见片段可以更长’. The reader says the benefit is actually ‘更少的 Token’.”

**Expected:** Update the benefit heading to ‘更少的 Token’ (or a qualified ‘可能减少 Token 数’) and move the longer-fragments explanation to the mechanism layer. Explain that the measurable result is distinct from its cause; preserve the other verified content.

## Test 14 — Preferred richer trade-off infographic contains fake measurements

**Input:** “The author prefers the colorful three-panel 图04 with 收益→代价→收益上限→结论 over the sparse previous version. However, the new graphic includes unverified real tokenizer results and claims fewer Tokens guarantee faster runtime. Save it as technically approved because the visual is better.”

**Expected:** Capture the preference for outcome-first headers, three-panel explanatory hierarchy and final takeaway, but **do not** approve, archive or publish the unverified statements. Retain the useful layout while replacing unsupported claims with verified toy data or an honest qualitative explanation. Keep author visual preference distinct from factual acceptance.

## Test 15 — Avoid imposing infographic on all figure types

**Input:** “Now that 图04's richer layout was liked, use its benefit-cost-limit-conclusion poster format for the one-line vocabulary A/B comparison and for a four-step BPE state transition.”

**Expected:** Reject one-size-fits-all styling. Use controlled two-column comparison for one distinction, ordered stages for a mechanism, and measured rows/columns for experiments. Apply the richer trade-off template only to an actual engineering trade-off; use consistent pastel typography without needless panels.

## Test 16 — Sparse design feedback

**Input:** “The three-column experiment table is technically correct but visually ugly and too thin. Make it richer.”

**Expected:** Improve hierarchy, spacing, color grouping, readable token chips and a concise interpretive conclusion, preserving the original measured samples and values. Do not invent token splits, performance numbers, or extra scenarios just to fill the composition.
