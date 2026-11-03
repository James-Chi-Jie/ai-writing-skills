# Critical reading and comparison checklist

## Claim extraction
- [ ] Have I read the primary full text / version and relevant experiment section, or disclosed the unverified scope?
- [ ] What is the author's precise question, and what is the strongest claim they make?
- [ ] Which components have working code? Which are conceptual? Which are production-proven?
- [ ] Which dates, reported numbers, negative results and limitations matter?

## Prior-art comparison
- [ ] What closest publicly documented system(s) should a knowledgeable reader compare?
- [ ] Are dates, capabilities, design scope, available code and evaluation conditions comparable?
- [ ] Is each allegedly new aspect a known idea, an original implementation, a new combination, or only a conjecture?
- [ ] Am I attributing an original contribution fairly without insisting everything is “old”?

## Benchmark integrity
- [ ] Does the baseline **actually exercise** the capability under comparison (e.g. delegate to Subagents)?
- [ ] Are model, prompts, tools, resource budget, samples and tasks comparable?
- [ ] What are p50/p95 and other metrics measuring? How many runs and what uncertainty?
- [ ] Are there simulated tasks or proxy measurements rather than real work?
- [ ] Does latency improve at the expense of Token, compute, human oversight, reliability or errors?
- [ ] Is the conclusion restricted to what this particular experiment supports?

## Hype and decision
- [ ] Are reports of popularity sourced and dated? Are proposed *causes* clearly marked as inferences?
- [ ] What would a technically experienced reader learn that is not already common knowledge?
- [ ] What evidence would falsify or materially revise the conclusion?
- [ ] Is a user asking for adoption guidance? Then include operational constraints, risks and verification steps.

## Example: DeepSeek Super-agent

Possible misleading shortcut: quote p95 = 15.7 minutes vs 29.5 minutes and conclude Super-agent beats conventional mature multi-agent systems. First check whether the “single Session + Subagent” baseline actually used Subagents in the relevant trials, whether the coding workload was simulated, the comparison setup, and Token cost. Architecture novelty must be evaluated against earlier Supervisor/Worker and persistent-agent implementations. If a source cannot be rechecked, disclose it rather than restating an unverified numeric result as established fact.
