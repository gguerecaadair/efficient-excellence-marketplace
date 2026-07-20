---
name: routing
description: Model-routing policy for efficient excellence. Use at the start of a task to triage it — decide how to split the work and which model tier does each part. Opus triages; simple sub-tasks (tables, lookups, bulk reading, routine edits) go to Sonnet/Haiku; complex sub-tasks (planning, architecture, review, hard synthesis, hard code) go to Fable/Opus.
---

# Efficient excellence — triage every request, route each sub-task

The **Opus** hub triages every request: read it, break it into sub-tasks, and hand each sub-task to the cheapest tier that will still do it *excellently*. Quality is the driver; cost is saved by not over-spending on the simple parts — never by under-serving the hard parts.

## Who does what
| Sub-task | Model | Agent |
|---|---|---|
| Triage, decomposition, coordination, synthesis, hard/correctness-sensitive code | **Opus 4.8** | hub · heavy-worker |
| Bulk reading, find/trace across many files, discovery | **Haiku** | scout |
| Table generation, formatting, simple Q&A, routine edits, straightforward code, running tests | **Sonnet 5** | worker |
| Plans, architecture, adversarial & methodology reviews, complex synthesis, hard decisions | **Fable** | planner |
| Verification pass before important work ships | **Opus** routine · **Fable** high-stakes | reviewer |

## Triage rules
1. **Simple → cheap.** A table, a lookup, a small edit, bulk reading → Sonnet or Haiku. Never spend Fable or Opus on something a cheaper tier does just as well.
2. **Complex → high quality.** Real reasoning, planning, architecture, review, hard synthesis → Fable; hard code → Opus.
3. **When unsure, escalate** — a wasted Opus/Fable call costs less than a shallow result shipped.
4. **Pin the model on every delegation** (haiku / sonnet / opus / fable) as well as relying on the agent's own setting.
5. **Keep briefs tight and point at specific files** — an isolated Fable/Opus agent told to "read the codebase" cold-reads it at premium rates. Scout first (Haiku), then hand the summary up.
6. Subagent effort in an agent definition overrides the session effort, which is why the cheap tiers stay economical even when the session runs at xhigh.

## Deliverable guardrails
When a sub-task produces customer-facing or report-shaped output (reports, cards, HTML, spec claims): draft and assemble on one tier (don't stitch fragments from different isolated agents), and inline the team's editorial standards into any subagent brief — subagents don't see the conversation, memory, or project instructions unless told. Hand a reviewer the rubric and source-of-truth files, not just the draft.
