---
name: routing
description: Model-routing policy for efficient excellence. Use at the start of a task to triage it — decide how to split the work and which model tier does each part. Opus triages; simple sub-tasks (tables, lookups, bulk reading, routine edits) go to Sonnet/Haiku; complex sub-tasks (planning, architecture, review, hard synthesis, hard code) go to Fable/Opus.
---

# Efficient excellence — triage every request, route each sub-task

The **Opus** hub triages every request: break it into sub-tasks and hand each to the cheapest tier that still does it *excellently*. Quality drives; cost is saved by not over-spending on the simple parts — never by under-serving the hard parts.

## Who does what
| Sub-task | Model | Agent |
|---|---|---|
| Triage, synthesis, hard/correctness-sensitive code | **Opus 4.8** | hub · heavy-worker |
| Bulk reading, find/trace across files, discovery | **Haiku** | scout |
| Tables, formatting, simple Q&A, routine edits, straightforward code, tests | **Sonnet 5** | worker |
| Plans, architecture, adversarial & methodology review, complex synthesis, hard decisions | **Fable** | planner |
| Verification before ship | **Opus** / **Fable** (high-stakes) | reviewer |

## Triage rules
1. **Simple → cheap** (Sonnet/Haiku); **complex → high quality** (Fable; hard code → Opus). When unsure, escalate — a wasted premium call beats a shallow result shipped.
2. **Pin the model on every delegation.** A `CLAUDE_CODE_SUBAGENT_MODEL` env var, if ever set, silently overrides all pins and flattens every tier onto one model — keep it unset.
3. **Every brief quotes the user's actual request verbatim in a QUOTE block.** Spokes see only what you pass them; an un-quoted brief lets a single misread propagate to planner, worker, and reviewer unchecked.
4. **Scout first, then hand the summary up — but the summary is a map, not ground truth.** The planner/worker re-reads the load-bearing files itself before committing.
5. **A spoke return missing its EVIDENCE / COVERAGE / UNVERIFIED sections is a failed delegation** — send it back rather than trust a plausible summary. Honour an `ESCALATE:` return by moving that sub-task up a tier.

## Deliverables
When a sub-task produces customer-facing or report-shaped output, draft and assemble on one tier (fragments from different isolated spokes drift in voice and rule-adherence), inline your team's editorial standards into the brief, and hand the reviewer the rubric and source-of-truth files, not just the draft.

## Note on subagent context
Subagents auto-load the CLAUDE.md hierarchy, a git snapshot, and any skills named in their definition — but not the conversation or the hub's memory. So put standing rules in CLAUDE.md (they reach every spoke) and pass task-specific facts in the brief. Keep CLAUDE.md lean: it's re-read into every non-fork subagent on every spawn.
